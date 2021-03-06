---
title: Azure マネージド アプリケーションの定義を作成する | Microsoft Docs
description: 組織のメンバーを対象とする Azure マネージド アプリケーションを作成する方法について説明します。
services: managed-applications
author: tfitzmac
ms.service: managed-applications
ms.devlang: na
ms.topic: quickstart
ms.tgt_pltfrm: na
ms.date: 10/04/2018
ms.author: tomfitz
ms.openlocfilehash: 1f80d7e63d994f0e3eb3733b99afaa1b056f4686
ms.sourcegitcommit: 9eaf634d59f7369bec5a2e311806d4a149e9f425
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2018
ms.locfileid: "48804914"
---
# <a name="publish-an-azure-managed-application-definition"></a>Azure マネージド アプリケーションの定義を発行する

このクイック スタートでは、マネージド アプリケーションの操作の概要を説明します。 組織のユーザー向けの内部カタログにマネージド アプリケーション定義を追加します。 導入を簡素化するために、マネージド アプリケーション用のファイルが既に作成されています。 これらのファイルは GitHub で入手できます。 これらのファイルを作成する方法については、[サービス カタログ アプリケーションの作成](publish-service-catalog-app.md)に関するチュートリアルをご覧ください。

最終的には、マネージド アプリケーションの定義を含んだ **appDefinitionGroup** という名前のリソース グループが作成されます。

[!INCLUDE [cloud-shell-try-it.md](../../includes/cloud-shell-try-it.md)]

## <a name="create-a-resource-group-for-definition"></a>定義用のリソース グループの作成

マネージド アプリケーション定義はリソース グループに存在します。 リソース グループは、Azure リソースをまとめてデプロイして管理するための論理上のコレクションです。

リソース グループを作成するには、次のコマンドを使用します。

```azurecli-interactive
az group create --name appDefinitionGroup --location westcentralus
```

## <a name="create-the-managed-application-definition"></a>マネージド アプリケーション定義の作成

マネージド アプリケーションを定義するときは、コンシューマーに代わってリソースを管理するユーザー、グループ、またはアプリケーションを選択します。 この ID には、割り当てられているロールに従って、マネージド リソース グループに対するアクセス許可が付与されています。 通常は、リソースを管理する Azure Active Directory グループを作成します。 ただし、この記事では独自の ID を使用します。

ID のオブジェクト ID を取得するには、次のコマンドでユーザー プリンシパル名を指定します。

```azurecli-interactive
userid=$(az ad user show --upn-or-object-id example@contoso.org --query objectId --output tsv)
```

次に、ユーザーにアクセス権を付与する RBAC の組み込みロールのロール定義 ID が必要となります。 次のコマンドは、所有者ロールのロール定義 ID を取得する方法を示しています。

```azurecli-interactive
roleid=$(az role definition list --name Owner --query [].name --output tsv)
```

次に、マネージド アプリケーション定義のリソースを作成します。 マネージド アプリケーションには、ストレージ アカウントだけが含まれます。

```azurecli-interactive
az managedapp definition create \
  --name "ManagedStorage" \
  --location "westcentralus" \
  --resource-group appDefinitionGroup \
  --lock-level ReadOnly \
  --display-name "Managed Storage Account" \
  --description "Managed Azure Storage Account" \
  --authorizations "$userid:$roleid" \
  --package-file-uri "https://raw.githubusercontent.com/Azure/azure-managedapp-samples/master/samples/201-managed-storage-account/managedstorage.zip"
```

コマンドが完了すると、リソース グループにマネージド アプリケーション定義が作成されます。 

前の例で使用されているパラメーターは次のとおりです。

* **resource-group**: マネージド アプリケーション定義が作成されるリソース グループの名前。
* **lock-level**: マネージド リソース グループに対して設定されるロックの種類。 これによって、このリソース グループに対して問題となるような操作を顧客が実行できないようにします。 現在サポートされているロック レベルは ReadOnly だけです。 ReadOnly が指定されている場合、マネージド リソース グループに存在するリソースの読み取りしか顧客は実行できません。 マネージド リソース グループへのアクセス権が付与されている発行元 ID は、ロックの対象外となります。
* **authorizations**: マネージド リソース グループへのアクセス許可を付与する際に使うプリンシパル ID とロール定義 ID を記述します。 `<principalId>:<roleDefinitionId>` の形式で指定します。 複数の値が必要な場合は、`<principalId1>:<roleDefinitionId1> <principalId2>:<roleDefinitionId2>` という形式で指定します。 このとき値は、スペースで区切って指定します。
* **package-file-uri**: 必要なファイルが含まれた .zip パッケージの場所。 このパッケージには、**mainTemplate.json** ファイルと **createUiDefinition.json** ファイルが含まれている必要があります。 **mainTemplate.json** には、マネージド アプリケーションの一部として作成される Azure リソースが定義されます。 テンプレートは、通常の Resource Manager テンプレートと違いはありません。 **createUiDefinition.json** では、ポータルを使用してマネージド アプリケーションを作成するユーザー向けのユーザー インターフェイスを生成します。

## <a name="next-steps"></a>次の手順

マネージド アプリケーション定義を発行しました。 今度は、その定義のインスタンスをデプロイする方法を確認しましょう。

> [!div class="nextstepaction"]
> [クイック スタート: サービス カタログ アプリのデプロイ](deploy-service-catalog-quickstart.md)