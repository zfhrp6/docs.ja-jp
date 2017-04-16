---
title: "Developing Windows Service Applications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ServiceInstaller class, Windows Service applications"
  - "Service class, Windows Service applications"
  - "Windows Service applications"
  - "Windows NT services"
  - "ServiceProcessInstaller class, Windows Service applications"
  - "services"
  - ".NET applications, Windows applications"
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: 18
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 18
---
# Developing Windows Service Applications
[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] または Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK を使用すると、サービスとしてインストールされるアプリケーションを作成することで、簡単にサービスを作成できます。  このアプリケーションは Windows サービスと呼ばれます。  フレームワーク機能を使用して、サービスを作成およびインストールできます。また、起動や停止など、サービスの動作制御を行うこともできます。  
  
> [!WARNING]
>  C\+\+ の Windows サービスのテンプレートは、Visual Studio 2010 に含まれていませんでした。  Windows サービスを作成するには、Visual C\# マネージ コードのサービスを作成することも、既存必要に応じて C\+\+ コードと相互運用することも、[ATL プロジェクト ウィザード](../Topic/ATL%20Project%20Wizard.md)を使用してネイティブ C\+\+ の Windows サービスを作成できます Visual Basic。  
  
## このセクションの内容  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 サービス アプリケーションが通常のプロジェクトとの違い Windows サービス アプリケーションの概要、サービスの有効期間ついて説明します。  
  
 [チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 サービスの作成例を [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] および Visual C\# で説明します。  
  
 [サービス アプリケーションのプログラミング アーキテクチャ](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 サービスのプログラミングに使用する言語要素について説明します。  
  
 [方法 : Windows サービスを作成する](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Windows サービス プロジェクトのテンプレートを使用して Windows サービスを作成および構成するプロセスについて説明します。  
  
## 関連項目  
 <xref:System.ServiceProcess.ServiceBase>  
 サービスの作成に使用される <xref:System.ServiceProcess.ServiceBase> クラスの主な機能について説明します。  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 サービスのインストールおよびアンインストールのために <xref:System.ServiceProcess.ServiceInstaller> クラスと共に使用される、<xref:System.ServiceProcess.ServiceProcessInstaller> クラスの機能について説明します。  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 サービスのインストールおよびアンインストールのために <xref:System.ServiceProcess.ServiceProcessInstaller> クラスと共に使用される、<xref:System.ServiceProcess.ServiceInstaller> クラスの機能について説明します。  
  
 [テンプレートからのプロジェクトの作成](http://msdn.microsoft.com/ja-jp/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 この章で使用されているプロジェクトの種類と、プロジェクトの種類の選び方について説明します。