---
title: オンプレミスの Azure AD パスワード保護に関する FAQ
description: オンプレミスの Azure AD パスワード保護に関する FAQ
services: active-directory
ms.service: active-directory
ms.subservice: authentication
ms.topic: article
ms.date: 02/01/2019
ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: jsimmons
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4d3b0f7cdacfb781ba7925be8146c10919c5269b
ms.sourcegitcommit: 75fef8147209a1dcdc7573c4a6a90f0151a12e17
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2019
ms.locfileid: "56455536"
---
# <a name="preview-azure-ad-password-protection-on-premises---frequently-asked-questions"></a>更新:オンプレミスの Azure AD パスワード保護 - よく寄せられる質問

|     |
| --- |
| Azure AD のパスワード保護は、Azure Active Directory のパブリック プレビュー機能です。 詳細については、「[Microsoft Azure プレビューの追加使用条件](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)」を参照してください。|
|     |

## <a name="general-questions"></a>一般的な質問

**Q:Azure AD パスワード保護はいつ一般提供 (GA) されますか?**

GA は、Q1 CY2019 を予定しています (2019 年 3 月末より前)。 今までこの機能に関するフィードバックを提供してくださった皆さん、どうもありがとうございました。感謝しております。

**Q:安全なパスワードを選択する方法に関して、ユーザーにどのようなガイダンスが与えられますか?**

このトピックに関する Microsoft の現在のガイダンスについては、次のリンクを参照してください。

[Microsoft のパスワードのガイダンス](https://www.microsoft.com/en-us/research/publication/password-guidance)

**Q:オンプレミスの Azure AD パスワード保護はパブリックでないクラウドでサポートされますか?**

いいえ。オンプレミスの Azure AD パスワード保護は、パブリック クラウドでのみサポートされます。 パブリックでないクラウドの提供開始についての日付は発表されていません。

**Q:どのようにして Azure AD パスワード保護の利点を自分のオンプレミスのユーザーのサブセットに適用できますか?**

サポートされていません。 デプロイして有効にされると、Azure AD パスワード保護では識別を行いません。すべてのユーザーがセキュリティの利点を等しく受け取ります。

**Q:その他のパスワード フィルター ベースの製品とサイド バイ サイドで Azure AD パスワード保護をインストールすることはサポートされていますか?**

はい。 複数の登録されたパスワード フィルター DLL に対するサポートは、コア Windows 機能であり、Azure AD パスワード保護に固有のものではありません。 登録されたパスワード フィルター DLL はすべて、パスワードを受け入れる前に一致している必要があります。

**Q:Azure を使用せずに、Active Directory 環境に Azure AD パスワード保護をデプロイし、構成するにはどうすればよいですか?**

サポートされていません。 Azure AD パスワード保護は、オンプレミスの Active Directory 環境への拡張をサポートする Azure の機能です。

**Q:Active Directory レベルでポリシーの内容を変更するにはどうすればよいですか?**

サポートされていません。 ポリシーは、Azure AD 管理ポータルを使用してのみ管理できます。 前の質問も参照してください。

**Q:sysvol レプリケーションに DFSR が必要なのはなぜですか?**

FRS (DFSR に対する先行テクノロジ) には、多くの既知の問題があり、より新しいバージョンの Windows Server Active Directory ではまったくサポートされていません。 Azure AD パスワード保護のゼロ テストは、FRS で構成されたドメインで行われます。

詳細については、次の記事を参照してください。

[sysvol レプリケーションを DFSR に移行するケース](https://blogs.technet.microsoft.com/askds/2010/04/22/the-case-for-migrating-sysvol-to-dfsr)

[FRS の終了が近づいています](https://blogs.technet.microsoft.com/filecab/2014/06/25/the-end-is-nigh-for-frs)

**Q:機能には、ドメイン sysvol 共有にどのくらいのディスク領域が必要ですか?**

正確な領域の使用量は、Microsoft グローバル禁止リストとテナントごとのカスタム リストで禁止されているトークンの数と長さ、および暗号化オーバーヘッドなどの要素に依存するため、さまざまに異なります。 これらのリストの内容は、将来拡大する可能性があります。 このことを念頭に、妥当な予想として、機能には、ドメイン sysvol 共有に最低 5 メガバイトの領域が必要になります。

**Q:DC エージェント ソフトウェアのインストールまたはアップグレードに再起動が必要なのはなぜですか?**

これはコア Windows 動作によって必要になります。

**Q:特定のプロキシ サーバーを使用するように DC エージェントを構成する方法はありますか?**

いいえ。 プロキシ サーバーはステートレスであるため、特定のどのプロキシ サーバーを使用するかは重要ではありません。

**Q:Azure AD Connect などの他のサービスと並行して Azure AD パスワード保護プロキシ サービスをデプロイしても大丈夫ですか?**

はい。 Azure AD パスワード保護プロキシ サービスと Azure AD Connect は、互いに直接競合することはありません。

**Q:この機能のデプロイによって、ドメイン コントローラーに対するパフォーマンスの打撃を懸念する必要がありますか?**

Azure AD パスワード保護 DC エージェント サービスは、既存の正常な Active Directory デプロイにおいてドメイン コントローラーのパフォーマンスに著しく影響を及ぼすことはないはずです。

ほとんどの Active Directory デプロイで、パスワード変更操作は、特定のどのドメイン コントローラーでもワークロード全体のごく一部になります。 たとえば、10000 ユーザー アカウントと 30 日に設定された MaxPasswordAge ポリシーがある Active Directory ドメインを想像してください。 平均で、このドメインでは毎日 10000/30 = 333 回までのパスワード変更操作が発生しますが、これは 1 つのドメイン コントローラーの場合でも少ない操作数です。 可能性のある最悪のケースのシナリオを考えてみます。1 時間に 1 つの DC でこの 333 回までのパスワードの変更が行われたとします。 たとえば、月曜日の朝に多数の従業員が全員出勤してくる場合に、このシナリオが発生する可能性があります。 この場合でも、333 回まで/60 分 = 1 分あたり 6 回のパスワードの変更が発生することになり、これも同様に重大な負荷ではありません。

ただし現在のドメイン コントローラーが既にパフォーマンス制限付きレベルで実行している (たとえば、CPU、ディスク領域、ディスク I/O に関して最大限に達しているなど) 場合は、この機能をデプロイする前に、ドメイン コン ローラーを追加するか、または使用可能なディスク領域を拡張することをお勧めします。 sysvol ディスク領域の使用量に関する上記の質問も参照してください。

**Q:ドメイン内のほんの一部の DC で Azure AD パスワード保護をテストしたいと思います。ユーザー パスワードの変更で、これらの特定の DC を強制的に使用させることはできますか?**

いいえ。 Windows クライアント OS は、ユーザーがパスワードを変更するときに、どのドメイン コントローラーを使用するかを制御します。 ドメイン コントローラーは、Active Directory サイトとサブネット割り当て、環境固有のネットワーク構成などの要素に基づいて選択されます。Azure AD パスワード保護は、これらの要素を制御せず、ユーザーのパスワードを変更するためにどのドメイン コントローラーが選択されるかに影響を与えることはできません。

この目標に部分的に到達する 1 つの方法は、特定の Active Directory サイト内のすべてのドメイン コントローラーに Azure AD パスワード保護をデプロイすることです。 このアプローチは、そのサイトに割り当てられる Windows クライアントに対し、したがってそれらのクライアントにログインし、パスワードを変更するユーザーに対しても、妥当なカバレッジを提供します。

**Q:プライマリ ドメイン コントローラー (PDC) にだけ Azure AD パスワード保護 DC エージェント サービスをインストールした場合、ドメイン内の他のすべてのドメイン コントローラーも保護されますか?**

いいえ。 PDC 以外の特定のドメイン コントローラーで、ユーザーのパスワードが変更された場合、クリアテキスト パスワードは PDC に送信されません (この考えは一般的な誤解です)。 特定の DC で、新しいパスワードが受け入れられると、その DC はそのパスワードを使用して、そのパスワードのさまざまな認証プロトコル固有のハッシュを作成し、ディレクトリでそれらのハッシュを保持します。 クリア テキスト パスワードは保持されません。 更新されたハッシュが、PDC にレプリケートされます。 場合により、ユーザー パスワードは、ネットワーク トポロジや Active Directory サイトの設計などのさまざまな要素に応じて、PDC で直接変更されることがあります。 (前の質問を参照してください。)

まとめると、PDC への Azure AD パスワード保護 DC エージェント サービスのデプロイでは、ドメイン全体で 100% の機能のセキュリティ カバレッジに到達する必要があります。 PDC のみへの機能のデプロイでは、ドメイン内の他の DC に対して、Azure AD パスワード保護のセキュリティ上の利点を提供しません。

**Q:Azure AD パスワード保護で、System Center Operations Manager 管理パックは使用できますか?**

いいえ。

## <a name="additional-content"></a>追加コンテンツ

次のリンクは、主要な Azure AD パスワード保護ドキュメントに含まれませんが、機能の有用な追加の情報源になる場合があります。

[Email Phishing Protection Guide – Part 15:Implement the Microsoft Azure AD Password Protection Service (for On-Premises too!)](https://blogs.technet.microsoft.com/cloudready/2018/10/14/email-phishing-protection-guide-part-15-implement-the-microsoft-azure-ad-password-protection-service-for-on-premises-too/) (電子メールのフィッシング保護ガイド – パート 15: Microsoft Azure AD パスワード保護サービス (オンプレミスの場合も))

[Azure AD Password Protection and Smart Lockout are now in Public Preview!](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Azure-AD-Password-Protection-and-Smart-Lockout-are-now-in-Public/ba-p/245423#M529) (Azure AD パスワード保護およびスマート ロックアウトがパブリック プレビュー段階になりました)

## <a name="microsoft-premierunified-support-training-available"></a>Microsoft Premier\Unified サポート トレーニングの提供開始

Azure AD パスワード保護の詳細と環境へのデプロイに興味がある場合は、Premier または Unified サポート契約のお客様が利用可能なマイクロソフト事前対応型サービスを利用できます。 サービスは、Azure Active Directory:パスワード保護と呼ばれます。 詳細については、テクニカル アカウント マネージャーにお問い合わせください。

## <a name="next-steps"></a>次の手順

ここでは回答されていないオンプレミスの Azure AD パスワード保護に関するご質問がある場合、以下のフィードバック項目を送信してください。

[Azure AD のパスワード保護をデプロイする](howto-password-ban-bad-on-premises-deploy.md)
