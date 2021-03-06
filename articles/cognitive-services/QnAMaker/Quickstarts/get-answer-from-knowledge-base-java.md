---
title: クイック スタート:ナレッジ ベースから回答を取得する - REST (Java) - QnA Maker
titlesuffix: Azure Cognitive Services
description: この Java REST ベースのクイック スタートでは、ナレッジ ベースからプログラムによって回答を取得する手順を紹介しています。
services: cognitive-services
author: diberry
manager: nitinme
ms.service: cognitive-services
ms.subservice: qna-maker
ms.topic: quickstart
ms.date: 11/19/2018
ms.author: diberry
ms.openlocfilehash: 5cdec31775258b4748609e994cc5455dc24eb1e2
ms.sourcegitcommit: 90cec6cccf303ad4767a343ce00befba020a10f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55863280"
---
# <a name="get-answers-to-a-question-from-a-knowledge-base-with-java"></a>Java を使用してナレッジ ベースから質問の回答を取得する

このクイック スタートでは、発行済みの QnA Maker ナレッジ ベースからプログラムによって回答を取得する手順を紹介しています。 QnA Maker は、[データ ソース](../Concepts/data-sources-supported.md)の FAQ などの半構造化コンテンツから質問とその回答を自動的に抽出します。 質問は JSON 形式になっており、API 要求の本文で送信されます。 

## <a name="prerequisites"></a>前提条件

* [JDK SE](https://aka.ms/azure-jdks) (Java Development Kit Standard Edition)
* このサンプルでは、HTTP Components の Apache [HTTP クライアント](http://hc.apache.org/httpcomponents-client-ga/)を使用しています。 以下の Apache HTTP クライアント ライブラリをプロジェクトに追加する必要があります。 
    * httpclient-4.5.3.jar
    * httpcore-4.4.6.jar
    * commons-logging-1.2.jar
* [Visual Studio Code](https://code.visualstudio.com/)
* [QnA Maker サービス](../How-To/set-up-qnamaker-service-azure.md)が必要です。 キーを取得するには、QnA Maker リソースの Azure ダッシュボードで、**[リソース管理]** の **[キー]** を選択します。 
* **[発行]** ページの設定。 発行済みのナレッジ ベースがない場合は、空のナレッジ ベースを作成し、**[設定]** ページでナレッジ ベースをインポートして発行してください。 [こちらの基本的なナレッジ ベース](https://github.com/Azure-Samples/cognitive-services-sample-data-files/blob/master/qna-maker/knowledge-bases/basic-kb.tsv)をダウンロードしてご使用ください。 

    発行ページの設定には、POST ルート値、Host 値、EndpointKey 値が含まれています。 

    ![Publish settings](../media/qnamaker-quickstart-get-answer/publish-settings.png)

このクイック スタートのコードは、[https://github.com/Azure-Samples/cognitive-services-qnamaker-java](https://github.com/Azure-Samples/cognitive-services-qnamaker-java/tree/master/documentation-samples/quickstarts/get-answer) リポジトリに存在します。 

## <a name="create-a-java-file"></a>java ファイルを作成する

VSCode を開いて、`GetAnswer.java` という名前の新しいファイルを作成し、次のクラスを追加します。

```Java
public class GetAnswer {

    public static void main(String[] args) 
    {

    }
}
```

## <a name="add-the-required-dependencies"></a>必要な依存関係を追加する

このクイック スタートでは、HTTP 要求に関する Apache のクラスを使用します。 プロジェクトに必要な依存関係を GetAnswer クラスの上 (`GetAnswer.java` ファイルの一番上) に追加します。

[!code-java[Add the required dependencies](~/samples-qnamaker-java/documentation-samples/quickstarts/get-answer/GetAnswer.java?range=5-13 "Add the required dependencies")]

## <a name="add-the-required-constants"></a>必要な定数を追加する

`GetAnswer.java` クラスの上部に、QnA Maker にアクセスするために必要な定数を追加します。 これらの値は、ナレッジ ベースを発行した後、**[発行]** ページにあります。  

[!code-java[Add the required constants](~/samples-qnamaker-java/documentation-samples/quickstarts/get-answer/GetAnswer.java?range=26-42 "Add the required constants")]

## <a name="add-a-post-request-to-send-question"></a>質問を送信するための POST 要求を追加する

次のコードは、ナレッジ ベースに質問を送信するための HTTPS 要求を QnA Maker API に送信し、その応答を受信するものです。

[!code-java[Add a POST request to send question to knowledge base](~/samples-qnamaker-java/documentation-samples/quickstarts/get-answer/GetAnswer.java?range=44-72 "Add a POST request to send question to knowledge base")]

`Authorization` ヘッダーの値には、文字列 `EndpointKey ` が含まれています。 

## <a name="build-and-run-the-program"></a>プログラムをビルドして実行する

コマンド ラインでプログラムをビルドし、実行します。 QnA Maker API に要求が自動的に送信され、コンソール ウィンドウへの出力が行われます。

1. ファイルをビルドします。

    ```bash
    javac -cp "lib/*" GetAnswer.java
    ```

1. ファイルを実行します。

    ```bash
    java -cp ".;lib/*" GetAnswer
    ```

[!INCLUDE [JSON request and response](../../../../includes/cognitive-services-qnamaker-quickstart-get-answer-json.md)] 


[!INCLUDE [Clean up files and knowledge base](../../../../includes/cognitive-services-qnamaker-quickstart-cleanup-resources.md)] 

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [QnA Maker (V4) REST API リファレンス](https://westus.dev.cognitive.microsoft.com/docs/services/5a93fcf85b4ccd136866eb37/operations/5ac266295b4ccd1554da75ff)
