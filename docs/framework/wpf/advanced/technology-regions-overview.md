---
title: "技術領域の概要 | Microsoft Docs"
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
  - "空域"
  - "相互運用性 [WPF], 空域"
  - "Win32 コード, 空域"
  - "Win32 コード, ウィンドウ領域"
  - "Win32 コード, WPF 相互運用"
  - "ウィンドウ領域"
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 技術領域の概要
WPF、Win32、DirectX など、複数のプレゼンテーション テクノロジを 1 つのアプリケーションで使用する場合、それらのテクノロジでは共通のトップレベル ウィンドウ内のレンダリング領域を共有する必要があります。  このトピックでは、WPF 相互運用アプリケーションのプレゼンテーションや入力に影響を与える可能性がある問題について説明します。  
  
## 領域  
 トップレベル ウィンドウ内では、相互運用アプリケーションのテクノロジの 1 つを構成する HWND のそれぞれに独自の領域 \("空域" とも呼ばれます\) がある、と考えることができます。  ウィンドウ内の各ピクセルはただ 1 つの HWND に属しており、これがその HWND の領域を構成します   \(厳密に言えば、複数の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND が存在する場合には複数の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 領域が存在しますが、ここでは説明しやすくするために、存在する領域は 1 つだけであると仮定します\)。  領域は、アプリケーションの有効期間中にそのピクセルの上に描画を試行するすべての層またはその他のウィンドウが、同じ描画レベル テクノロジの一部である必要があることを意味しています。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 上で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ピクセルを描画しようとすると、望ましくない結果が生じるため、相互運用 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] によって可能な限り禁止されています。  
  
### 領域の例  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]、および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が混在するアプリケーションを次の図に示します。  それぞれのテクノロジは別個の、重複しないピクセルのセットを使用しているので、領域の問題は発生しません。  
  
 ![空域の問題がないウィンドウ](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle01.png "MigrationInteropArchitectArticle01")  
  
 このアプリケーションでマウス ポインターの位置を使用して、これら 3 つのどの領域の上にも描画を試みるアニメーションを作成するとします。  アニメーション自体をどのテクノロジが担当するとしても、そのテクノロジは他の 2 つの領域に違反することになります。  Win32 の領域の上に WPF の円の描画を試みる場合を次の図に示します。  
  
 ![相互運用ダイアグラム](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle02.png "MigrationInteropArchitectArticle02")  
  
 領域の違反は、異なるテクノロジの間で透明度\/アルファ ブレンドを使用した場合にも発生します。  次の図では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のボックスが [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] および [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] の領域に違反しています。  この [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ボックス内のピクセルは半透明であるため、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] と [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の両方によって共通に所有されている必要がありますが、それは不可能です。  したがって、これも領域の違反となり、作成できません。  
  
 ![相互運用ダイアグラム](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle03.png "MigrationInteropArchitectArticle03")  
  
 前の 3 つの例では四角形領域を使用しましたが、別の形状を使用することもできます。  たとえば、領域に穴を使用できます。  四角形の穴がある [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] の領域を次の図に示します。これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] の領域を結合したサイズです。  
  
 ![相互運用ダイアグラム](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle04.png "MigrationInteropArchitectArticle04")  
  
 領域は、次の図のように、まったく四角形でない図形や、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] の HRGN \(領域\) で記述できる任意の図形にすることもできます。  
  
 ![相互運用ダイアグラム](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle05.png "MigrationInteropArchitectArticle05")  
  
## 透過性とトップレベル ウィンドウ  
 Windows でのウィンドウ マネージャーは、実際には [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] の HWND のみを処理します。  したがって、それぞれの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> は HWND です。  <xref:System.Windows.Window> HWND は、すべての HWND の一般規則に従う必要があります。  その HWND 内で、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コードは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 全体がサポートすることであれば、すべて実行できます。  しかし、デスクトップ上で他の HWND と対話する場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] の処理と描画の規則に従う必要があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] の非四角形ウィンドウ用 HRGN と、ピクセルごとのアルファ情報をサポートするレイヤード ウィンドウを使用することで、四角形以外のウィンドウをサポートします。  
  
 一定のアルファおよびカラー キーはサポートされません。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] のレイヤード ウィンドウの機能は、プラットフォームによって異なります。  
  
 レイヤード ウィンドウでは、ウィンドウ内のすべてのピクセルに適用するアルファ値を指定することで、ウィンドウ全体を半透明にすることができます   \([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] は実際にはピクセルごとのアルファをサポートしていますが、このモードでは、ダイアログやドロップダウンなどを含むすべての子 HWND を開発者自身で描画する必要があるため、これを実用プログラムで使用することは非常に困難です\)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は HRGN をサポートしますが、この機能に対応するマネージ [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] はありません。  プラットフォーム呼び出しおよび <xref:System.Windows.Interop.HwndSource> を使用すると、関連する [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を呼び出すことができます。  詳細については、「[マネージ コードからのネイティブ関数の呼び出し](../Topic/Calling%20Native%20Functions%20from%20Managed%20Code.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイヤード ウィンドウの機能は、オペレーティング システムによってさまざまに異なります。  これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では描画に [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] が使用されますが、レイヤード ウィンドウは [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] レンダリングではなく、主に [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] レンダリング用に設計されているためです。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] 以降では、ハードウェアで加速されたレイヤード ウィンドウをサポートします。  ハードウェアで加速されたレイヤード ウィンドウを [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] 上で使用するには、[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] によるサポートが必要となるため、この機能は、実行するマシンの [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] のバージョンに依存します。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、特にレンダリングがハードウェアで加速されている場合、要求された正確な色を描画することを保証できないため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、透明度カラー キーをサポートしません。  
  
-   アプリケーションを [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] で実行している場合、レイヤード ウィンドウを [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] サーフェイス上で実行すると、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] アプリケーションでの描画時に、ちらつきが発生します   \(実際のレンダリング シーケンスでは、まず [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] がレイヤード ウィンドウを非表示にし、次に [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] が描画を実行した後、[!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] がレイヤード ウィンドウを元に戻します\)。  この制限は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 以外のレイヤード ウィンドウでも同じです。  
  
## 参照  
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [チュートリアル: Win32 での WPF クロックのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-clock-in-win32.md)   
 [WPF での Win32 コンテンツのホスト](../../../../docs/framework/wpf/advanced/hosting-win32-content-in-wpf.md)