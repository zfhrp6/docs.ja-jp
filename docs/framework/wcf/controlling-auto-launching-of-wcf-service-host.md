---
title: "WCF サービス ホストの自動起動の制御 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WcfOptions"
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# WCF サービス ホストの自動起動の制御
[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ソリューションに複数のプロジェクトが含まれている場合、既定では、同じソリューション内の別のプロジェクトをデバッグするときでも、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクトの [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス ホスト \(WcfSvcHost.exe\) が自動的に起動します。この自動起動機能は制御できます。  
  
 これを行うには、**ソリューション エクスプローラー**で [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス プロジェクトを右クリックし、**\[プロパティ\]** をクリックして、**\[WCF オプション\]** タブをクリックします。既定では、**\[同じソリューション内での別のプロジェクトのデバッグ時に WCF サービス ホストを開始する\]** チェック ボックスがオンになっています。チェック ボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを起動しないように指定できます。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクト  
  
-   シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
-   ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
-   配信サービス ライブラリ プロジェクト  
  
## 参照  
 [WCF サービス ホスト \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)