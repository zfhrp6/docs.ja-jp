---
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809889"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF サービス ホストの自動起動の制御
複数のプロジェクトを含む同じ Visual Studio ソリューション内の別のプロジェクトをデバッグするときに、WCF サービス ライブラリ プロジェクトの Windows Communication Foundation (WCF) サービス ホスト (WcfSvcHost.exe) の自動起動する機能を制御できます。  
  
 これを行うには、プロジェクトを右クリックして、WCF サービスで**ソリューション エクスプ ローラー**、選択**プロパティ**、 をクリック**WCF オプション** タブ。**開始 WCF サービス ホスト、同じソリューション内の別のプロジェクトをデバッグするときに** チェック ボックスが既定で有効にします。 ボックスをオフに、同じソリューション内の別のプロジェクトのデバッグ時に、この特定のプロジェクトの WCF サービス ホストが起動しないようにします。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
-   WCF サービス ライブラリ プロジェクト。  
  
-   シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
-   ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
-   配信サービス ライブラリ プロジェクト  
  
## <a name="see-also"></a>関連項目  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
