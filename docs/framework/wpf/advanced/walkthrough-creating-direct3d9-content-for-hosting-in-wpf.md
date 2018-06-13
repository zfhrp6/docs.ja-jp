---
title: 'チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: f279fb1749be9953e6d09d4b1bd4dd8578d42615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547369"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成
このチュートリアルでは、Windows Presentation Foundation (WPF) アプリケーションでホストするために適切な Direct3D9 コンテンツを作成する方法を示します。 WPF アプリケーションで Direct3D9 コンテンツをホストの詳細については、次を参照してください。 [WPF と Direct3D9 相互運用](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)です。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   Direct3D9 プロジェクトを作成します。  
  
-   Direct3D9 プロジェクトを WPF アプリケーションのホスト用に構成します。  
  
 完了したら、WPF アプリケーションで使用するための Direct3D9 コンテンツを含んでいる DLL があります。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
-   DirectX SDK 9or 以降。  
  
## <a name="creating-the-direct3d9-project"></a>Direct3D9 プロジェクトを作成します。  
 最初の手順を作成し、Direct3D9 プロジェクトを構成します。  
  
#### <a name="to-create-the-direct3d9-project"></a>Direct3D9 プロジェクトを作成するには  
  
1.  C という名前で新しい Win32 プロジェクトを作成`D3DContent`です。  
  
     Win32 アプリケーション ウィザードが開き、ようこそ画面を表示します。  
  
2.  **[次へ]** をクリックします。  
  
     アプリケーション設定 画面が表示されます。  
  
3.  **アプリケーションの種類:**  セクションで、select、 **DLL**オプション。  
  
4.  **[完了]** をクリックします。  
  
     D3DContent プロジェクトが生成されます。  
  
5.  ソリューション エクスプ ローラーで、D3DContent プロジェクトを右クリックして**プロパティ**です。  
  
     **D3DContent プロパティ ページ** ダイアログ ボックスが表示されます。  
  
6.  選択、 **C/C++** ノード。  
  
7.  **追加のインクルード ディレクトリ**フィールドで、DirectX の場所を含めるフォルダーを指定します。 このフォルダーの既定の場所は %ProgramFiles%\Microsoft DirectX SDK (*バージョン*) \Include です。  
  
8.  ダブルクリックして、**リンカー**ノードを展開します。  
  
9. **追加のライブラリ ディレクトリ**フィールドで、DirectX のライブラリ フォルダーの場所を指定します。 このフォルダーの既定の場所は %ProgramFiles%\Microsoft DirectX SDK (*バージョン*) \Lib\x86 です。  
  
10. 選択、**入力**ノード。  
  
11. **追加の依存関係**フィールドに、追加、`d3d9.lib`と`d3dx9.lib`ファイル。  
  
12. ソリューション エクスプ ローラーで、新しいモジュール定義 (.def) という名前のファイルを追加`D3DContent.def`をプロジェクトにします。  
  
## <a name="creating-the-direct3d9-content"></a>Direct3D9 コンテンツを作成します。  
 最適なパフォーマンスを得るに Direct3D9 コンテンツは、特定の設定を使用する必要があります。 次のコードでは、最適なパフォーマンス特性を備えた Direct3D9 画面を作成する方法を示します。 詳細については、次を参照してください。 [Direct3D9 と WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)です。  
  
#### <a name="to-create-the-direct3d9-content"></a>コンテンツを作成、Direct3D9  
  
1.  ソリューション エクスプ ローラーを使用して、次の名前のプロジェクトに 3 つの C++ クラスを追加します。  
  
     `CRenderer` (で仮想デストラクター)  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  Renderer.h コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  Renderer.cpp コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  RendererManager.h コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  RendererManager.cpp コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  TriangleRenderer.h コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  TriangleRenderer.cpp コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  Stdafx.h コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. Dllmain.cpp コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. コード エディターで D3DContent.def を開きます。  
  
11. 自動的に生成されたコードを次のコードに置き換えます。  
  
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
  
## <a name="next-steps"></a>次の手順  
  
-   WPF アプリケーションで Direct3D9 コンテンツをホストします。 詳細については、次を参照してください。[チュートリアル: wpf Direct3D9 のコンテンツをホストしている](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Interop.D3DImage>  
 [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [チュートリアル: WPF での Direct3D9 コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
