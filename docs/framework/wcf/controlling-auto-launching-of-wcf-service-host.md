---
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: fe936ee3ff42b586c733de597de808b86f3e2575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF サービス ホストの自動起動の制御
Windows Communication Foundation (WCF) サービス ホスト (WcfSvcHost.exe) の自動起動する機能を制御することができます、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービス ライブラリ プロジェクト、複数のプロジェクトを含む同じ Visual Studio ソリューション内の別のプロジェクトをデバッグする場合.  
  
 これを行うを右クリックし、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]でサービス プロジェクト**ソリューション エクスプ ローラー**、選択**プロパティ**、 をクリック**WCF オプション**タブです。**開始 WCF サービス ホスト、同じソリューション内の別のプロジェクトをデバッグするときに** チェック ボックスが既定で有効にします。 チェック ボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを起動しないように指定できます。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクト  
  
-   シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
-   ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
-   配信サービス ライブラリ プロジェクト  
  
## <a name="see-also"></a>関連項目  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
