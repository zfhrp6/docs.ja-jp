---
title: Windows サービス アプリケーションの開発
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: 18
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 325e43f4b1734bc6ab8753285e5069f36b0fda51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="developing-windows-service-applications"></a>Windows サービス アプリケーションの開発
Microsoft[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]または Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK、簡単にサービスを作成できますが、サービスとしてインストールされているアプリケーションを作成しています。 この種類のアプリケーションには、Windows サービスが呼び出されます。 フレームワーク機能を使用することができますサービスを作成、したり、インストールし、開始、停止、および動作を制御します。  
  
> [!WARNING]
>  C++ の Windows サービス テンプレートは、Visual Studio 2010 に組み込まれませんでした。 Windows サービスを作成するには、Visual c# または Visual Basic は、必要な場合は、既存の C++ コードと相互運用する可能性があります、マネージ コードでサービスを作成することができますか、またはを使用して、ネイティブ C++ で Windows サービスを作成することができます、 [ATLプロジェクトウィザード](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 サービス、およびその他の一般的なプロジェクトの種類のサービス アプリケーションの違いの有効期間の Windows サービス アプリケーションの概要を説明します。  
  
 [チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 サービスを作成する例を示します[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]および Visual c# です。  
  
 [サービス アプリケーションのプログラミング アーキテクチャ](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 サービスのプログラミングで使用される言語要素をについて説明します。  
  
 [方法 : Windows サービスを作成する](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 作成して、Windows サービス プロジェクトのテンプレートを使用して Windows サービスの構成のプロセスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 <xref:System.ServiceProcess.ServiceBase>  
 主要な機能について説明します、<xref:System.ServiceProcess.ServiceBase>クラスは、サービスを作成するために使用します。  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 機能について説明します、<xref:System.ServiceProcess.ServiceProcessInstaller>と共に使用されるクラス、<xref:System.ServiceProcess.ServiceInstaller>クラスをインストールして、サービスをアンインストールします。  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 機能について説明します、<xref:System.ServiceProcess.ServiceInstaller>と共に使用されるクラス、<xref:System.ServiceProcess.ServiceProcessInstaller>クラスをインストールおよびサービスをアンインストールします。  
  
 [NIB テンプレートからプロジェクトの作成](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 プロジェクトをについて説明します。 この章でし、それらの間を選択する方法で使用される型。
