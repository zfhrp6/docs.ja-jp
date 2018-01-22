---
title: "チュートリアル : WPF での Direct3D9 コンテンツのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ad6ac99a77e3477499a871e269cc7faa7a59f12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>チュートリアル : WPF での Direct3D9 コンテンツのホスト
このチュートリアルでは、Windows Presentation Foundation (WPF) アプリケーションで Direct3D9 コンテンツをホストする方法を示します。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   Direct3D9 コンテンツをホストする WPF プロジェクトを作成します。  
  
-   Direct3D9 コンテンツをインポートします。  
  
-   使用して Direct3D9 コンテンツを表示、<xref:System.Windows.Interop.D3DImage>クラスです。  
  
 完了したら、WPF アプリケーションで Direct3D9 コンテンツをホストする方法がわかります。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
-   DirectX SDK 9 以降。  
  
-   WPF と互換性のある形式で Direct3D9 コンテンツを含む DLL です。 詳細については、次を参照してください。 [WPF と Direct3D9 相互運用](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)と[チュートリアル: WPF でのホストの Direct3D9 のコンテンツを作成する](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)です。  
  
## <a name="creating-the-wpf-project"></a>WPF プロジェクトを作成します。  
 最初の手順では、WPF アプリケーションのプロジェクトを作成します。  
  
#### <a name="to-create-the-wpf-project"></a>WPF プロジェクトを作成するには  
  
-   新しい WPF アプリケーション プロジェクトを作成するには名前付き Visual c# で`D3DHost`です。 詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。  
  
     MainWindow.xaml を開きます、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
## <a name="importing-the-direct3d9-content"></a>Direct3D9 コンテンツをインポートします。  
 使用してアンマネージ DLL から Direct3D9 コンテンツをインポートする、`DllImport`属性。  
  
#### <a name="to-import-direct3d9-content"></a>Direct3D9 コンテンツをインポートするには  
  
1.  MainWindow.xaml.cs をコード エディターで開きます。  
  
2.  自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Direct3D9 コンテンツをホストしています。  
 最後に、使用して、 <xref:System.Windows.Interop.D3DImage> Direct3D9 コンテンツをホストするクラス。  
  
#### <a name="to-host-the-direct3d9-content"></a>Direct3D9 コンテンツをホストするには  
  
1.  MainWindow.xaml で自動的に生成された XAML を次の XAML に置き換えます。  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  プロジェクトをビルドします。  
  
3.  Bin/debug フォルダーに Direct3D9 コンテンツを含んでいる DLL をコピーします。  
  
4.  F5 キーを押してプロジェクトを実行します。  
  
     WPF アプリケーション内で Direct3D9 コンテンツが表示されます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Interop.D3DImage>  
 [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
