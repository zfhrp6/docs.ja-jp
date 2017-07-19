---
title: "チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成 | Microsoft Docs"
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
  - "Direct3D9 [WPF 相互運用性], 作成 (Direct3D9 コンテンツを)"
  - "WPF, 作成 (Direct3D9 コンテンツを)"
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成
このチュートリアルでは、Windows Presentation Foundation \(WPF\) アプリケーションでのホストに適した Direct3D9 コンテンツを作成する方法を示します。  WPF アプリケーションで Direct3D9 コンテンツをホストする方法の詳細については、「[WPF と Direct3D9 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)」を参照してください。  
  
 このチュートリアルでは次のタスクを行います。  
  
-   Direct3D9 プロジェクトを作成する。  
  
-   WPF アプリケーションでホストするための Direct3D9 プロジェクトを構成する。  
  
 タスクが終了すると、WPF アプリケーションで使用される Direct3D9 コンテンツを含む DLL が生成されます。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX SDK 9 以降  
  
## Direct3D9 プロジェクトの作成  
 最初に Direct3D9 プロジェクトを作成して構成します。  
  
#### Direct3D9 プロジェクトを作成するには  
  
1.  C\+\+ で、`D3DContent` という名前の新しい Win32 プロジェクトを作成します。  
  
     Win32 アプリケーション ウィザードが開き、\[ようこそ\] 画面が表示されます。  
  
2.  **\[次へ\]** をクリックします。  
  
     \[アプリケーションの設定\] 画面が表示されます。  
  
3.  **\[アプリケーションの種類\]** セクションで、**\[DLL\]** オプションをクリックします。  
  
4.  **\[完了\]** をクリックします。  
  
     D3DContent プロジェクトが生成されます。  
  
5.  ソリューション エクスプローラーで、D3DContent プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  
  
     **\[D3DContent プロパティ ページ\]** ダイアログ ボックスが表示されます。  
  
6.  **\[C\/C\+\+\]** ノードをクリックします。  
  
7.  **\[追加のインクルード ディレクトリ\]** フィールドに、DirectX インクルード フォルダーの場所を指定します。  このフォルダーの既定の場所は、%ProgramFiles%\\Microsoft DirectX SDK \(*バージョン*\)\\Include です。  
  
8.  **\[リンカー\]** ノードをダブルクリックして展開します。  
  
9. **\[追加のライブラリ ディレクトリ\]** フィールドに、DirectX ライブラリ フォルダーの場所を指定します。  このフォルダーの既定の場所は、%ProgramFiles%\\Microsoft DirectX SDK \(*バージョン*\)\\Lib\\x86 です。  
  
10. **\[入力\]** ノードをクリックします。  
  
11. **\[追加の依存ファイル\]** フィールドに、`d3d9.lib` ファイルと `d3dx9.lib` ファイルを追加します。  
  
12. ソリューション エクスプローラーで、`D3DContent.def` という名前の新しいモジュール定義ファイル \(.def\) をプロジェクトに追加します。  
  
## Direct3D9 コンテンツの作成  
 最大限のパフォーマンスを得るには、Direct3D9 コンテンツで特定の設定を使用する必要があります。  次のコードは、最大限のパフォーマンス特性を持つ Direct3D9 サーフェイスを作成する方法を示しています。  詳細については、「[Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)」を参照してください。  
  
#### Direct3D9 コンテンツを作成するには  
  
1.  ソリューション エクスプローラーを使用して、3 つの C\+\+ クラスを次に示す名前のプロジェクトに追加します。  
  
     `CRenderer` \(仮想デストラクターを使用\)  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  コード エディターで Renderer.h を開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  コード エディターで Renderer.cpp を開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  コード エディターで RendererManager.h を開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  コード エディターで RendererManager.cpp を開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  コード エディターで TriangleRenderer.h を開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  コード エディターで TriangleRenderer.cpp を開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  コード エディターで stdafx.h を開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. コード エディターで dllmain.cpp を開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. コード エディターで D3DContent.def を開きます。  
  
11. 自動的に生成されたコードを次のコードで置き換えます。  
  
    ```  
  
    LIBRARY "D3DContent"  
  
    EXPORTS  
  
    SetSize  
    SetAlpha  
    SetNumDesiredSamples  
    SetAdapter  
  
    GetBackBufferNoRef  
    Render  
    Destroy  
  
    ```  
  
12. プロジェクトをビルドします。  
  
## 次の手順  
  
-   WPF アプリケーションで Direct3D9 コンテンツをホストします。  詳細については、「[チュートリアル : WPF での Direct3D9 コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Interop.D3DImage>   
 [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)   
 [チュートリアル : WPF での Direct3D9 コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)