---
author: cynthn
ms.service: virtual-machines-windows
ms.topic: include
ms.date: 10/26/2018
ms.author: cynthn
ms.openlocfilehash: 14abae6f6f72d724fffb1ccaa12f56fb6976f7a1
ms.sourcegitcommit: 6e09760197a91be564ad60ffd3d6f48a241e083b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50227459"
---
次の表に、Windows の一般化された OS イメージ (gen.) と特殊化された OS イメージ (spec.) のアップロードとキャプチャの考えられる組み合わせを示します。 エラーなしで処理される組み合わせは Y で示され、エラーがスローされる組み合わせは N で示されています。発生するさまざまなエラーの原因と解決策が表の下に記載されています。

| OS | spec. のアップロード | gen. のアップロード | spec. のキャプチャ | gen. のキャプチャ |
| --- | --- | --- | --- | --- |
| Windows gen. |N<sup>1</sup> |Y |N<sup>3</sup> |Y |
| Windows spec. |Y |N<sup>2</sup> |Y |N<sup>4</sup> |

