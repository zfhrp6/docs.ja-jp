---
title: Windows サービス アプリケーションの開発
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: af6e4bf7697b3139f6809295737fdd0d90b7f013
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512269"
---
# <a name="developing-windows-service-applications"></a>Windows サービス アプリケーションの開発
Microsoft Visual Studio または Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK を使用すると、サービスとしてインストールするアプリケーションを作成することで簡単に作成できます。 この種類のアプリケーションは、Windows サービスと呼ばれます。 フレームワーク機能を使用することで、サービスを作成、インストール、開始、停止したり、動作を制御したりできます。  
  
> [!WARNING]
>  C++ の Windows サービス テンプレートは、Visual Studio 2010 に含まれていませんでした。 Windows サービスを作成するには、Visual C# または Visual Basic のマネージド コードでサービスを作成するか (必要に応じて、既存の C++ コードと相互運用できます)、[ATL プロジェクト ウィザード](/cpp/atl/reference/atl-project-wizard)を使用して、ネイティブ C++ で Windows サービスを作成できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Windows サービス アプリケーションの概要、サービスの有効期間、およびサービスがその他の一般的な種類のプロジェクトどのように異なるかを説明します。  
  
 [チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Visual Basic および Visual C# でサービスを作成する例を提供します。  
  
 [サービス アプリケーションのプログラミング アーキテクチャ](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 サービスのプログラミングで使用される言語要素について説明します。  
  
 [方法 : Windows サービスを作成する](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Windows サービス プロジェクトのテンプレートを使用して Windows サービスを作成、構成するプロセスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 <xref:System.ServiceProcess.ServiceBase>  
 サービスの作成に使用される、<xref:System.ServiceProcess.ServiceBase> クラスの主要な機能を説明します。  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <xref:System.ServiceProcess.ServiceInstaller> クラスと共に使用して、サービスをインストール/アンインストールする <xref:System.ServiceProcess.ServiceProcessInstaller> クラスの機能について説明します。  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <xref:System.ServiceProcess.ServiceProcessInstaller> クラスと共に使用して、サービスをインストール/アンインストールする <xref:System.ServiceProcess.ServiceInstaller> クラスの機能について説明します。  
  
 [NIB テンプレートからのプロジェクトの作成](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 この章で使用されるプロジェクトの種類と、それを選択する際に役立つガイドラインを説明します。
