---
title: Azure Storage の概要 - Azure のクラウド ストレージ | Microsoft Docs
description: Azure Storage は、Microsoft のクラウド ストレージ ソリューションです。 Azure Storage は、高可用性、セキュリティ、持続性、高度なスケーラビリティ、および冗長性を備えた、データ オブジェクト向けのストレージを提供します。
services: storage
author: tamram
ms.service: storage
ms.topic: conceptual
ms.date: 01/02/2019
ms.author: tamram
ms.subservice: common
ms.openlocfilehash: d558f0fa5abc421785ff6f9fcc2a6318819e3ebc
ms.sourcegitcommit: 5839af386c5a2ad46aaaeb90a13065ef94e61e74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58012734"
---
# <a name="introduction-to-azure-storage"></a>Azure Storage の概要

Azure Storage は、最新のデータ ストレージ シナリオ用の Microsoft のクラウド ストレージ ソリューションです。 Azure Storage は、データ オブジェクトのための高度にスケーラブルなオブジェクト ストア、クラウドのためのファイル システム サービス、信頼性の高いメッセージングのためのメッセージング ストア、および NoSQL ストアを提供します。 Azure Storage の特徴を次に示します。

- **持続性と高可用性。** 冗長性により、一時的なハードウェア障害が発生した場合でも、データが安全に保たれます。 地域的な災害または自然災害から保護するために、データセンターまたは地理的リージョンにまたがってデータをレプリケートすることもできます。 この方法でレプリケートされたデータは、予期しない停止が発生した場合でも高可用性を維持します。 
- **セキュリティ保護。** Azure Storage に書き込まれたすべてのデータは、サービスによって暗号化されます。 Azure Storage では、データにアクセスできるユーザーをきめ細かく制御できます。
- **スケーラブル。** Azure Storage には、今日のアプリケーションのデータ ストレージとパフォーマンスに関するニーズを満たすために、高度にスケーラブルな設計が採用されています。 
- **マネージド。** Microsoft Azure では、ユーザーに代わって、ハードウェアのメンテナンス、更新、および重大な問題が処理されます。
- **アクセス可能。** Azure Storage 内のデータには、世界中のどこからでも HTTP または HTTPS 経由でアクセスできます。 Microsoft では、.NET、Java、Node.js、Python、PHP、Ruby、Go などのさまざまな言語の Azure Storage 用の SDK と、成熟した REST API を提供しています。 Azure Storage では、Azure PowerShell または Azure CLI によるスクリプトの実行がサポートされます。 また、Azure Portal と Azure Storage Explorer により、データを操作するための使いやすい視覚的ソリューションが提供されます。  

## <a name="azure-storage-services"></a>Azure Storage サービス

Azure Storage には、次のデータ サービスが含まれます。 

- [Azure BLOB](../blobs/storage-blobs-introduction.md):テキストおよびバイナリ データのための高度にスケーラブルなオブジェクト ストア。
- [Azure ファイル](../files/storage-files-introduction.md):クラウドまたはオンプレミスのデプロイ用のマネージド ファイル共有。
- [Azure キュー](../queues/storage-queues-introduction.md):アプリケーション コンポーネント間の信頼性の高いメッセージングのためのメッセージング ストア。 
- [Azure テーブル](../tables/table-storage-overview.md):構造化データのスキーマレス ストレージのための NoSQL ストア。

それぞれのサービスには、ストレージ アカウントを通じてアクセスします。 作業を開始するには、「[ストレージ アカウントの作成](storage-quickstart-create-account.md)」を参照してください。

## <a name="blob-storage"></a>BLOB ストレージ

Azure Blob Storage は、Microsoft のクラウド用オブジェクト ストレージ ソリューションです。 BLOB ストレージは、テキスト データやバイナリ データなどの大量の非構造化データを格納するために最適化されています。 

BLOB ストレージは、次の目的に最適です。

* 画像またはドキュメントをブラウザーに直接配信する。
* 分散アクセス用にファイルを格納する。
* ビデオおよびオーディオをストリーミング配信する。
* バックアップと復元、ディザスター リカバリー、アーカイブのためのデータを格納する。
* オンプレミス サービスまたは Azure ホステッド サービスで分析するデータを格納する。

BLOB ストレージ内のオブジェクトには、世界中のどこからでも HTTP または HTTPS 経由でアクセスできます。 ユーザーまたはクライアント アプリケーションは、URL、[Azure Storage REST API](https://docs.microsoft.com/rest/api/storageservices/blob-service-rest-api)、[Azure PowerShell](https://docs.microsoft.com/powershell/module/azure.storage)、[Azure CLI](https://docs.microsoft.com/cli/azure/storage)、または Azure Storage クライアント ライブラリを介して BLOB にアクセスできます。 ストレージ クライアント ライブラリは、[.NET](https://docs.microsoft.com/dotnet/api/overview/azure/storage/client)、[Java](https://docs.microsoft.com/java/api/overview/azure/storage/client)、[Node.js](https://azure.github.io/azure-storage-node)、[Python](https://azure-storage.readthedocs.io/)、[PHP](https://azure.github.io/azure-storage-php/)、[Ruby](https://azure.github.io/azure-storage-ruby) など、さまざまな言語で利用できます。

Blob Storage の詳細については、「[Blob Storage の概要](../blobs/storage-blobs-introduction.md)」をご覧ください。

## <a name="azure-files"></a>Azure Files
[Azure Files](../files/storage-files-introduction.md) では、標準的なサーバー メッセージ ブロック (SMB) プロトコルを使用してアクセスできる可用性の高いネットワーク ファイル共有を設定することができます。 つまり、複数の VM が、読み取りアクセス権と書き込みアクセス権の両方を使用して同じファイルを共有できます。 また、REST インターフェイスまたはストレージ クライアント ライブラリを使用してファイルを読み取ることもできます。

Azure Files と企業のファイル共有上のファイルとの違いの 1 つは、世界中のどこからでも、ファイルを指し、共有アクセス署名 (SAS) トークンを含む URL を使用して、ファイルにアクセスできることです。 SAS トークンは生成することができます。SAS トークンを使用することで、特定の期間にわたってプライベートな資産への特定のアクセスを許可できます。

ファイル共有は、多くの一般的なシナリオで使用できます。

* 多くのオンプレミスのアプリケーションでファイル共有が使用されます。 この機能により、データを共有するそれらのアプリケーションを Azure に簡単に移行できます。 オンプレミスのアプリケーションで使用されているのと同じドライブ文字にファイル共有をマウントすることにより、ファイル共有にアクセスするアプリケーションの部分は、(変更があっても) 最小限の変更で動作します。

* 構成ファイルをファイル共有に格納して、複数の VM からアクセスできます。 グループ内の複数の開発者によって使用されるツールやユーティリティをファイル共有に格納できるため、だれでもそれらを見つけ、同じバージョンを使用することができます。

* ファイル共有に書き込んだ後で処理または分析できるデータの例として、診断ログ、メトリック、およびクラッシュ ダンプの 3 つが挙げられます。

Active Directory ベースの認証およびアクセス制御リスト (ACL) は現時点でサポートされていませんが、将来的にサポートされる予定です。 ファイル共有へのアクセスの認証を提供するために、ストレージ アカウントの資格情報が使用されます。 これは、共有をマウントしている全員に、共有に対する完全な読み取り/書き込みアクセス権が与えられることを意味します。

Azure Files の詳細については、「[Azure Files の概要](../files/storage-files-introduction.md)」を参照してください。

## <a name="queue-storage"></a>ストレージ

Azure Queue サービスは、メッセージの保管と取得に使用します。 キューに許容されるメッセージ サイズは最大 64 KB で、1 つのキューに数百万件のメッセージを格納することができます。 一般に、非同期的に処理するメッセージのリストを格納するのがキューの用途となります。

たとえば、画像をアップロードしてそれぞれにサムネイルを作成する機能をユーザーに提供するとしましょう。 もちろん画像のアップロードの際、サムネイルを作成するまでユーザーに待ってもらうことはできます。 しかし、その代わりの方法として、キューを使うこともできます。 ユーザーからのアップロードが完了したら、メッセージをキューに書き込みます。 その後、Azure Functions でキューからメッセージを取得して、サムネイルを作成するのです。 この処理では、各段階を個別にスケーリングすることができるので、用途に応じたチューニングの自由度が高まります。

Azure キューの詳細については、「[キューの概要](../queues/storage-queues-introduction.md)」を参照してください。

## <a name="table-storage"></a>テーブル ストレージ

Azure Cosmos DB に、新たに Azure Table Storage が加わりました。 Azure Table Storage のドキュメントについては、「[Azure Table Storage の概要](../tables/table-storage-overview.md)」を参照してください。 既存の Azure Table Storage サービスに加えて、スループットに最適化されたテーブル、グローバルな分散、自動セカンダリ インデックスを利用できる新しい Azure Cosmos DB Table API プランが追加されています。 詳細を確認し、新しい Premium 版を使ってみるには、[Azure Cosmos DB の Table API](https://aka.ms/premiumtables) に関する記事を参照してください。

テーブル ストレージの詳細については、「[Azure Table Storage の概要](../tables/table-storage-overview.md)」を参照してください。

## <a name="disk-storage"></a>Disk Storage

Azure Storage には、仮想マシンで使用されるマネージド ディスクと非管理対象ディスクの機能も含まれています。 これらの機能の詳細については、[コンピューティング サービスのドキュメント](https://docs.microsoft.com/azure/#pivot=products&panel=Compute)を参照してください。

## <a name="types-of-storage-accounts"></a>ストレージ アカウントの種類

[!INCLUDE [storage-account-types-include](../../../includes/storage-account-types-include.md)]

ストレージ アカウントの種類の詳細については、[Azure Storage アカウントの概要](storage-account-overview.md)に関するページを参照してください。 

## <a name="accessing-your-blobs-files-and-queues"></a>BLOB、ファイル、キューへのアクセス

各ストレージ アカウントには認証キーが 2 つあり、どちらを使っても、すべての操作を実行することができます。 キーが 2 つあるため、キーを時折ロール オーバーしてセキュリティを強化することができます。 アカウント名と共にキーを手に入れると、ストレージ アカウントのあらゆるデータに無制限でアクセスできるため、キーを安全に保つことがきわめて重要となります。

このセクションでは、ストレージ アカウントとそのデータのセキュリティを確保する 2 つの方法について説明します。 ストレージ アカウントとデータのセキュリティについて詳しくは、「[Azure Storage security guide (Azure Storage セキュリティ ガイド)](storage-security-guide.md)」を参照してください。

### <a name="securing-access-to-storage-accounts-using-azure-ad"></a>Azure AD を使ってストレージ アカウントへのアクセスのセキュリティを確保する

ストレージ データへのアクセスのセキュリティを確保する方法の 1 つとして、ストレージ アカウント キーへのアクセスを制御する方法が考えられます。 Resource Manager のロールベースのアクセス制御 (RBAC) を使って、ユーザー、グループ、アプリケーションのいずれかにロールを割り当てることができます。 これらのロールは、ひとまとめにして許可または禁止される一連の操作に関連付けられます。 RBAC を使ってストレージ アカウントへのアクセスを許可する場合、対象となるのは、そのストレージ アカウントの管理操作だけです (アクセス レベルを変更するなど)。 RBAC を使って、データ オブジェクト (特定のコンテナー、特定のファイル共有など) へのアクセスを許可することはできません。 ただし RBAC を使ってストレージ アカウント キーへのアクセスを許可したうえで、そのキーをデータ オブジェクトの読み取りに使用することはできます。

### <a name="securing-access-using-shared-access-signatures"></a>Shared Access Signature を使ってアクセスのセキュリティを確保する

データ オブジェクトのセキュリティは、Shared Access Signature と保存されているアクセス ポリシーを使って確保できます。 Shared Access Signature (SAS) は、セキュリティ トークンを含む文字列です。資産の URI にセキュリティ トークンをアタッチすることで、特定のストレージ オブジェクトへのアクセスを委任し、アクセス許可やアクセスの日時の範囲などの制約を指定することができます。 この機能には、さまざまな可能性があります。 詳細については、「[Using Shared Access Signatures (SAS) (Shared Access Signature (SAS) の使用)](storage-dotnet-shared-access-signature-part-1.md)」を参照してください。

### <a name="public-access-to-blobs"></a>BLOB へのパブリック アクセス

Blob service を通じて、コンテナーとその BLOB (または特定の BLOB) へのパブリック アクセスを提供することができます。 コンテナーまたは BLOB をパブリックとして指定すると、認証が不要になり、すべてのユーザーが匿名でリソースを読み取ることができます。 たとえば、Blob Storage に格納されている画像やビデオ、ドキュメントを使った Web サイトがある場合などにこの方法を利用できます。 詳細については、「[コンテナーと BLOB への匿名読み取りアクセスを管理する](../blobs/storage-manage-access-to-resources.md)」を参照してください。

## <a name="encryption"></a>暗号化

Storage サービスには、2 種類の基本的な暗号化を使用できます。 セキュリティと暗号化の詳細については、「[Azure Storage セキュリティ ガイド](storage-security-guide.md)」を参照してください。

### <a name="encryption-at-rest"></a>保存時の暗号化

保存時の Azure Storage Service Encryption (SSE) は、データを保護して安全性を確保し、組織のセキュリティとコンプライアンスの要件を満たすお手伝いをします。 この機能を使用すると、Azure Storage はストレージに保存する前にデータを自動的に暗号化し、取得する前に復号化します。 暗号化、復号化、キーの管理は、ユーザーにはまったく意識されずに行われます。


SSE は、すべてのパフォーマンス レベル (Standard および Premium)、すべてのデプロイ モデル (Azure Resource Manager とクラシック)、すべての Azure Storage サービス (BLOB、Queue、Table、File) のデータを自動的に暗号化します。 SSE は、Azure Storage のパフォーマンスに影響しません。

保存時の SSE 暗号化の詳細については、「[Azure Storage Service Encryption for Data at Rest](storage-service-encryption.md)」を参照してください。

### <a name="client-side-encryption"></a>クライアント側暗号化

ストレージ クライアント ライブラリのメソッドを呼び出すことで、プログラムによってデータを暗号化したうえで、クライアントからネットワーク経由で Azure に送信することができます。 データは暗号化された状態で保存されます。つまり、保存状態でも暗号化されます。 データを再度読み取るときは、その情報を受信した後で暗号化を解除することになります。

クライアント側の暗号化の詳細については、[.NET による Microsoft Azure Storage のクライアント側の暗号化](storage-client-side-encryption.md)に関するページを参照してください。

## <a name="redundancy"></a>冗長性

Azure Storage は、データの持続性を確保するために、データの複数のコピーをレプリケートします。 冗長性オプションは、ストレージ アカウントを設定するときに選択します。 

[!INCLUDE [storage-common-redundancy-options](../../../includes/storage-common-redundancy-options.md)]

ディザスター リカバリーの詳細については、「[Azure Storage の停止が発生した場合の対処方法](storage-disaster-recovery-guidance.md)」を参照してください。

## <a name="transferring-data-to-and-from-azure-storage"></a>Azure Storage との間のデータ転送

Azure Storage へのデータの移動または Azure Storage からのデータの移動には、いくつかのオプションがあります。 どのオプションを選択するかは、データセットとネットワーク帯域幅のサイズによって異なります。 詳細については、「[データ転送用の Azure ソリューションを選択する](storage-choose-data-transfer-solution.md)」を参照してください。

## <a name="pricing"></a>価格

Azure Storage の価格の詳細については、[価格のページ](https://azure.microsoft.com/pricing/details/storage/blobs/)を参照してください。

## <a name="storage-apis-libraries-and-tools"></a>ストレージ API、ライブラリ、ツール
Azure Storage のリソースは、HTTP/HTTPS 要求が可能な任意の言語からアクセスできます。 さらに、主要な複数の言語のプログラミング ライブラリも用意されています。 これらのライブラリを使用すると、同期呼び出しと非同期呼び出し、操作のバッチ処理、例外管理、自動再試行、実行動作などの詳細が処理され、Azure Storage の使用に関するさまざまな側面が簡略化されます。 ライブラリは、次の言語およびプラットフォーム用が現在提供されており、その他についても準備中です。

### <a name="azure-storage-data-api-and-library-references"></a>Azure Storage データ API およびライブラリのリファレンス
* [Storage サービス REST API](https://docs.microsoft.com/rest/api/storageservices/)
* [.NET 用ストレージ クライアント ライブラリ](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
* [Java/Android 用ストレージ クライアント ライブラリ](https://docs.microsoft.com/java/api/overview/azure/storage)
* [Node.js 用ストレージ クライアント ライブラリ](https://docs.microsoft.com/javascript/api/azure-storage)
* [Python 用ストレージ クライアント ライブラリ](https://github.com/Azure/azure-storage-python)
* [PHP 用ストレージ クライアント ライブラリ](https://github.com/Azure/azure-storage-php)
* [Ruby 用ストレージ クライアント ライブラリ](https://github.com/Azure/azure-storage-ruby)
* [C++ 用ストレージ クライアント ライブラリ](https://github.com/Azure/azure-storage-cpp)

### <a name="azure-storage-management-api-and-library-references"></a>Azure Storage 管理 API およびライブラリのリファレンス
* [ストレージ リソース プロバイダー REST API](https://docs.microsoft.com/rest/api/storagerp/)
* [.NET 用 Storage Resource Provider クライアント ライブラリ](https://docs.microsoft.com/dotnet/api/overview/azure/storage/management)
* [Storage Service Management REST API (Classic)](https://msdn.microsoft.com/library/azure/ee460790.aspx)

### <a name="azure-storage-data-movement-api-and-library-references"></a>Azure Storage データ移動 API およびライブラリのリファレンス
* [Storage Import/Export Service REST API](https://docs.microsoft.com/rest/api/storageimportexport/)
* [.NET 用 Storage Data Movement クライアント ライブラリ](https://docs.microsoft.com/dotnet/api/microsoft.windowsazure.storage.datamovement)

### <a name="tools-and-utilities"></a>ツールとユーティリティ
* [ストレージ用 Azure PowerShell コマンドレット](https://docs.microsoft.com/powershell/module/az.storage)
* [ストレージ用 Azure CLI コマンドレット](https://docs.microsoft.com/cli/azure/storage)
* [AzCopy コマンド ライン ユーティリティ](https://aka.ms/downloadazcopy)
* [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) は、Windows、macOS、Linux で Azure Storage のデータを視覚的に操作できる Microsoft 製の無料のスタンドアロン アプリです。
* [Azure Storage クライアント ツール](../storage-explorers.md)
* [Azure 開発者ツール](https://azure.microsoft.com/tools/)

## <a name="next-steps"></a>次の手順

Azure Storage を稼働させるには、[ストレージ アカウントの作成](storage-quickstart-create-account.md)に関するページを参照してください。
