---
title: Azure PowerShell のサンプル スクリプト - Azure 仮想マシンのバックアップ | Microsoft Docs
description: Azure PowerShell のサンプル スクリプト - Azure 仮想マシンのバックアップ
services: backup
documentationcenter: ''
author: rayne-wiselman
manager: carmonm
ms.service: backup
ms.topic: sample
ms.date: 01/31/2019
ms.author: raynew
ms.custom: mvc
ms.openlocfilehash: 915c5f6c8e8de1b5a7a7590ba41125cbff7b8f36
ms.sourcegitcommit: 5978d82c619762ac05b19668379a37a40ba5755b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2019
ms.locfileid: "55497640"
---
# <a name="back-up-an-encrypted-azure-virtual-machine-with-powershell"></a>PowerShell を使用して、暗号化された Azure 仮想マシンをバックアップする

このスクリプトでは、暗号化された Azure 仮想マシン用に geo 冗長ストレージ (GRS) で Recovery Services コンテナーを作成します。 既定の保護ポリシーはコンテナーに適用されます。 ポリシーによって仮想マシンの毎日のバックアップが生成され、バックアップはそれぞれ 30 日間保持されます。 また、このスクリプトによって、仮想マシンの最初の復旧ポイントがトリガーされ、その復旧ポイントは 365 日間保持されます。 

[!INCLUDE [sample-powershell-install](../../../includes/sample-powershell-install-no-ssh.md)]

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

## <a name="sample-script"></a>サンプル スクリプト

[!code-powershell[main](../../../powershell_scripts/backup/backup-encrypted-vm/backup-encrypted-vm.ps1 "Back up encrypted virtual machine")]

## <a name="clean-up-deployment"></a>デプロイのクリーンアップ 

次のコマンドを実行して、リソース グループ、VM、すべての関連リソースを削除します。

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

## <a name="script-explanation"></a>スクリプトの説明

このスクリプトでは、以下のコマンドを実行してデプロイを作成します。 表内の各項目は、コマンドごとのドキュメントにリンクされています。


| コマンド | メモ | 
|---|---| 
| [New-AzureRmResourceGroup](/powershell/module/azurerm.resources/new-azurermresourcegroup) | すべてのリソースを格納するリソース グループを作成します。 | 
| [New-AzureRmRecoveryServicesVault](/powershell/module/azurerm.recoveryservices/New-AzureRmRecoveryServicesVault) | バックアップを格納する Recovery Services コンテナーを作成します。 | 
| [Set-AzureRmRecoveryServicesBackupProperties](/powershell/module/azurerm.recoveryservices/Set-AzureRmRecoveryServicesBackupProperties) | Recovery Services コンテナーでバックアップ ストレージのプロパティを設定します。 | 
| [New-AzureRmRecoveryServicesBackupProtectionPolicy](/powershell/module/azurerm.recoveryservices.backup/new-azurermrecoveryservicesbackupprotectionpolicy)| Recovery Services コンテナーでスケジュール ポリシーと保有ポリシーを使用して、保護ポリシーを作成します。 | 
| [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) | サービス プリンシパルに暗号化キーへのアクセス権を付与するために、Key Vault に対するアクセス許可を設定します。 | 
| [Enable-AzureRmRecoveryServicesBackupProtection](/powershell/module/azurerm.recoveryservices.backup/enable-azurermrecoveryservicesbackupprotection) | 指定した Backup 保護ポリシーで項目のバックアップを有効にします。 | 
| [Set-AzureRmRecoveryServicesBackupProtectionPolicy](/powershell/module/azurerm.recoveryservices.backup/set-azurermrecoveryservicesbackupprotectionpolicy)| 既存の Backup 保護ポリシーを変更します。 | 
| [Backup-AzureRmRecoveryServicesBackupItem](/powershell/module/azurerm.recoveryservices.backup/backup-azurermrecoveryservicesbackupitem) | バックアップ スケジュールに関連付けられていない、保護された Azure Backup 項目のバックアップを開始します。 |
| [Wait-AzureRmRecoveryServicesBackupJob](/powershell/module/azurerm.recoveryservices.backup/wait-azurermrecoveryservicesbackupjob) | Azure Backup ジョブが終了するのを待機します。 | 
| [Remove-AzureRmResourceGroup](/powershell/module/azurerm.resources/remove-azurermresourcegroup) | リソース グループと、それに含まれているすべてのリソースを削除します。 | 

## <a name="next-steps"></a>次の手順

Azure PowerShell モジュールの詳細については、[Azure PowerShell のドキュメント](/powershell/azure/overview)を参照してください。

