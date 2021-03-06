---
title: Azure Application Gateway 上の Web アプリケーション ファイアウォール ルールのカスタマイズ - Azure CLI | Microsoft Docs
description: この記事では、Azure CLI を使用して Application Gateway 上で Web アプリケーション ファイアウォール ルールをカスタマイズする方法について説明します。
documentationcenter: na
services: application-gateway
author: vhorne
manager: jpconnock
editor: tysonn
ms.service: application-gateway
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.custom: ''
ms.workload: infrastructure-services
ms.date: 07/26/2017
ms.author: victorh
ms.openlocfilehash: 95eb0ef48f3e0cb6e835dc0582cc652f06315d44
ms.sourcegitcommit: e69fc381852ce8615ee318b5f77ae7c6123a744c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "55992859"
---
# <a name="customize-web-application-firewall-rules-through-the-azure-cli"></a>Azure CLI 2.0 を使用した Web アプリケーション ファイアウォール ルールのカスタマイズ

> [!div class="op_single_selector"]
> * [Azure Portal](application-gateway-customize-waf-rules-portal.md)
> * [PowerShell](application-gateway-customize-waf-rules-powershell.md)
> * [Azure CLI](application-gateway-customize-waf-rules-cli.md)

Azure Application Gateway Web アプリケーション ファイアウォール (WAF) は、Web アプリケーションを保護します。 こうした保護は、Open Web Application Security Project (OWASP) コア ルール セット (CRS) によって提供されます。 ルールによっては誤検出を発生させて、実際のトラフィックを妨げることがあります。 このため、Application Gateway には、ルール グループとルールをカスタマイズする機能が用意されています。 特定のルール グループおよびルールの詳細については、[Web アプリケーション ファイアウォールの CRS 規則グループと規則の一覧](application-gateway-crs-rulegroups-rules.md)に関するページを参照してください。

## <a name="view-rule-groups-and-rules"></a>ルール グループとルールの表示

以下のコード例は、構成可能なルールとルール グループを表示する方法を示しています。

### <a name="view-rule-groups"></a>ルール グループの表示

次の例は、ルール グループの表示方法を示しています。

```azurecli-interactive
az network application-gateway waf-config list-rule-sets --type OWASP
```

以下の出力は、前の例から返される応答を簡略化したものです。

```json
[
  {
    "id": "/subscriptions//resourceGroups//providers/Microsoft.Network/applicationGatewayAvailableWafRuleSets/",
    "location": null,
    "name": "OWASP_3.0",
    "provisioningState": "Succeeded",
    "resourceGroup": "",
    "ruleGroups": [
      {
        "description": "",
        "ruleGroupName": "REQUEST-910-IP-REPUTATION",
        "rules": null
      },
      ...
    ],
    "ruleSetType": "OWASP",
    "ruleSetVersion": "3.0",
    "tags": null,
    "type": "Microsoft.Network/applicationGatewayAvailableWafRuleSets"
  },
  {
    "id": "/subscriptions//resourceGroups//providers/Microsoft.Network/applicationGatewayAvailableWafRuleSets/",
    "location": null,
    "name": "OWASP_2.2.9",
    "provisioningState": "Succeeded",
    "resourceGroup": "",
   "ruleGroups": [
      {
        "description": "",
        "ruleGroupName": "crs_20_protocol_violations",
        "rules": null
      },
      ...
    ],
    "ruleSetType": "OWASP",
    "ruleSetVersion": "2.2.9",
    "tags": null,
    "type": "Microsoft.Network/applicationGatewayAvailableWafRuleSets"
  }
]
```

### <a name="view-rules-in-a-rule-group"></a>ルール グループ内のルールの表示

次の例は、指定されたルール グループ内のルールを表示する方法を示しています。

```azurecli-interactive
az network application-gateway waf-config list-rule-sets --group "REQUEST-910-IP-REPUTATION"
```

以下の出力は、前の例から返される応答を簡略化したものです。

```json
[
  {
    "id": "/subscriptions//resourceGroups//providers/Microsoft.Network/applicationGatewayAvailableWafRuleSets/",
    "location": null,
    "name": "OWASP_3.0",
    "provisioningState": "Succeeded",
    "resourceGroup": "",
    "ruleGroups": [
      {
        "description": "",
        "ruleGroupName": "REQUEST-910-IP-REPUTATION",
        "rules": [
          {
            "description": "Rule 910011",
            "ruleId": 910011
          },
          ...
        ]
      }
    ],
    "ruleSetType": "OWASP",
    "ruleSetVersion": "3.0",
    "tags": null,
    "type": "Microsoft.Network/applicationGatewayAvailableWafRuleSets"
  }
]
```

## <a name="disable-rules"></a>ルールの無効化

次の例は、アプリケーション ゲートウェイに対するルール `910018` および `910017` を無効にします。

```azurecli-interactive
az network application-gateway waf-config set --resource-group AdatumAppGatewayRG --gateway-name AdatumAppGateway --enabled true --rule-set-version 3.0 --disabled-rules 910018 910017
```

## <a name="next-steps"></a>次の手順

無効にするルールを構成したら、WAF ログを表示する方法を学習できます。 詳細については、[Application Gateway の診断](application-gateway-diagnostics.md#diagnostic-logging)に関するトピックを参照してください。

[fig1]: ./media/application-gateway-customize-waf-rules-portal/1.png
[1]: ./media/application-gateway-customize-waf-rules-portal/figure1.png
[2]: ./media/application-gateway-customize-waf-rules-portal/figure2.png
[3]: ./media/application-gateway-customize-waf-rules-portal/figure3.png
