---
title: WCF サービス ホストの自動起動の制御
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5bb6356ba4698cad00d443fdb80b1a45d35e2175
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF サービス ホストの自動起動の制御
自動起動する機能を制御する[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]サービス ホスト (WcfSvcHost.exe) を[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービス ライブラリ プロジェクト、複数のプロジェクトを含む同じ Visual Studio ソリューション内の別のプロジェクトをデバッグするときにします。  
  
 これを行うを右クリックし、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]でサービス プロジェクト**ソリューション エクスプ ローラー**、選択**プロパティ**、 をクリック**WCF オプション**タブです。**開始 WCF サービス ホスト、同じソリューション内の別のプロジェクトをデバッグするときに** チェック ボックスが既定で有効にします。 チェック ボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを起動しないように指定できます。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクト  
  
-   シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
-   ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
-   配信サービス ライブラリ プロジェクト  
  
## <a name="see-also"></a>関連項目  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
