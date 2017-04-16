---
title: "チュートリアル : WPF での Direct3D9 コンテンツのホスト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Direct3D9 [WPF 相互運用性], ホスト (Direct3D9 コンテンツを)"
  - "WPF, ホスト (Direct3D9 コンテンツを)"
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# チュートリアル : WPF での Direct3D9 コンテンツのホスト
このチュートリアルでは、Windows Presentation Foundation \(WPF\) アプリケーションで Direct3D9 コンテンツをホストする方法について説明します。  
  
 このチュートリアルでは次のタスクを行います。  
  
-   Direct3D9 コンテンツをホストする WPF プロジェクトを作成する。  
  
-   Direct3D9 コンテンツをインポートする。  
  
-   <xref:System.Windows.Interop.D3DImage> クラスを使用して Direct3D9 コンテンツを表示する。  
  
 このチュートリアルを終了すると、WPF アプリケーションで Direct3D9 コンテンツをホストする方法を理解できます。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX SDK 9 以降  
  
-   WPF 互換形式の Direct3D9 コンテンツを含む DLL。  詳細については、「[WPF と Direct3D9 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)」および「[チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)」を参照してください。  
  
## WPF プロジェクトの作成  
 最初に WPF アプリケーションのプロジェクトを作成します。  
  
#### WPF プロジェクトを作成するには  
  
-   Visual C\# で `D3DHost` という名前の新しい WPF アプリケーション プロジェクトを作成します。  詳細については、「[方法 : 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/ja-jp/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)」を参照してください。  
  
     [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]で MainWindow.xaml が開きます。  
  
## Direct3D9 コンテンツのインポート  
 `DllImport` 属性を使用して、Direct3D9 コンテンツをアンマネージ DLL からインポートします。  
  
#### Direct3D9 コンテンツをインポートするには  
  
1.  コード エディターで MainWindow.xaml.cs を開きます。  
  
2.  自動的に生成されたコードを次のコードで置き換えます。  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## Direct3D9 コンテンツのホスト  
 最後に、<xref:System.Windows.Interop.D3DImage> クラスを使用して Direct3D9 コンテンツをホストします。  
  
#### Direct3D9 コンテンツをホストするには  
  
1.  MainWindow.xaml で、自動的に生成された XAML を次の XAML に置き換えます。  
  
     [!code-xml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  プロジェクトをビルドします。  
  
3.  Direct3D9 コンテンツを含む DLL を bin\/Debug フォルダーにコピーします。  
  
4.  F5 キーを押してプロジェクトを実行します。  
  
     WPF アプリケーションの中に Direct3D9 コンテンツが表示されます。  
  
## 参照  
 <xref:System.Windows.Interop.D3DImage>   
 [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)