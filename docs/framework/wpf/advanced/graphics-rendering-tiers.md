---
title: "グラフィックスの描画層 | Microsoft Docs"
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
  - "グラフィックスの描画層"
  - "グラフィックス, パフォーマンス"
  - "グラフィックス, 描画層"
  - "描画 (グラフィックスを)"
  - "描画層"
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
caps.latest.revision: 44
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 43
---
# グラフィックスの描画層
描画層は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを実行するデバイスのグラフィックス ハードウェアの機能およびパフォーマンスのレベルを定義します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="graphics_hardware"></a>   
## グラフィックス ハードウェア  
 描画層のレベルに大きく影響するグラフィックス ハードウェアの機能は、次のとおりです。  
  
-   **ビデオ RAM** グラフィックス ハードウェアのビデオ メモリの量によって、グラフィックスを合成する際に使用できるバッファーのサイズと数が決まります。  
  
-   **ピクセル シェーダー** ピクセル シェーダーは、ピクセル単位で効果を計算するグラフィックス処理関数です。  表示するグラフィックスの解像度によっては、各表示フレームの処理に数百万ピクセルが必要な場合もあります。  
  
-   **頂点シェーダー** 頂点シェーダーは、オブジェクトの頂点データの算術演算を実行するグラフィックス処理関数です。  
  
-   **マルチテクスチャのサポート** マルチテクスチャがサポートされていると、3D グラフィックス オブジェクトのブレンド操作を行うときに、2 つ以上の別個のテクスチャを適用できます。  マルチテクスチャのサポートの度合いは、グラフィックス ハードウェアのマルチテクスチャ ユニットの数によって決まります。  
  
<a name="rendering_tier_definitions"></a>   
## 描画層の定義  
 グラフィックス ハードウェアの機能によって、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの表示能力が決まります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] システムは、次の 3 つの描画階層を定義します。  
  
-   **描画層 0** グラフィックス ハードウェアの加速が使用されません。  すべてのグラフィックス機能で、ソフトウェア アクセラレータを使用します。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] のバージョン レベルは Version 9.0 未満です。  
  
-   **描画層 1** 一部のグラフィックス機能で、グラフィックス ハードウェア アクセラレータを使用します。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] のバージョン レベルは Version 9.0 以上です。  
  
-   **描画層 2** ほとんどのグラフィックス機能でグラフィックス ハードウェアの加速を使用します。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] のバージョン レベルは Version 9.0 以上です。  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=fullName> プロパティを使用すると、アプリケーションの実行時に描画層を取得できます。  描画層を使用すると、特定のハードウェア アクセラレータ グラフィックス機能がデバイスでサポートされているかどうかを確認できます。  アプリケーションは、デバイスでサポートされている描画層に応じて、実行時に異なるコード パスを受け取ることができます。  
  
### 描画層 0  
 描画層の値 0 は、デバイスのアプリケーションに使用できるグラフィックス ハードウェア アクセラレータがないことを示します。  この描画層では、すべてのグラフィックスがハードウェア アクセラレータを使用せずにソフトウェアで描画されることを想定する必要があります。  この層の機能は、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] の 9.0 未満の Version に対応します。  
  
### 描画層 1 および描画層 2  
  
> [!NOTE]
>  .NET Framework 4 以降、描画層 1 は、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 以降をサポートするグラフィックス ハードウェアのみを含むように再定義されています。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 または 8 をサポートするグラフィックス ハードウェアは、描画層 0 と定義されています。  
  
 描画層の値 1 または 2 は、必要なシステム リソースが使用可能であり、枯渇していない場合に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のほとんどのグラフィックス機能がハードウェア アクセラレータを使用することを示します。  これは、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] の 9.0 以上の Version に対応します。  
  
 描画層 1 と描画層 2 のグラフィックス ハードウェア要件の違いを次の表に示します。  
  
|機能|層 1|層 2|  
|--------|---------|---------|  
|[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] のバージョン|9.0 以上であることが必要です。|9.0 以上であることが必要です。|  
|ビデオ RAM|60 MB 以上であることが必要です。|120 MB 以上であることが必要です。|  
|ピクセル シェーダー|バージョン レベルは、2.0 以上であることが必要です。|バージョン レベルは、2.0 以上であることが必要です。|  
|頂点シェーダー|要件は特にありません。|バージョン レベルは、2.0 以上であることが必要です。|  
|マルチテクスチャ単位|要件は特にありません。|単位数は、4 以上であることが必要です。|  
  
 描画層 1 および描画層 2 では、以下の機能がハードウェア アクセラレータによって加速されます。  
  
|機能|説明|  
|--------|--------|  
|2D レンダリング|ほとんどの 2D レンダリングがサポートされています。|  
|3D ラスタライズ|ほとんどの 3D ラスタライズがサポートされています。|  
|3D 異方性フィルタリング|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、3D コンテンツの描画時に異方性フィルタリングの使用が試行されます。  異方性フィルタリングとは、カメラから遠く、視線角度のきつい位置にあるサーフェイス上のテクスチャの画質を向上させる手法です。|  
|3D ミップマップ|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、3D コンテンツの描画時にミップマップの使用が試行されます。ミップマップを使用すると、テクスチャが <xref:System.Windows.Controls.Viewport3D> の狭い視野を占める場合にテクスチャの描画品質が向上します。|  
|放射状グラデーション|サポートされますが、大きなオブジェクトでは <xref:System.Windows.Media.RadialGradientBrush> を使用しないでください。|  
|3D の光源計算|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、頂点ごとの光源処理を実行します。そのため、メッシュに適用されている各素材の頂点ごとに光の強さを計算する必要があります。|  
|テキストの描画|サブピクセル フォントの描画では、グラフィックス ハードウェアで利用可能なピクセル シェーダーを使用します。|  
  
 描画層 2 に対してのみ、以下の機能がハードウェア アクセラレータによって加速されます。  
  
|機能|説明|  
|--------|--------|  
|3D アンチエイリアシング|3D アンチエイリアシングは、Windows Display Driver Model \(WDDM\) をサポートするオペレーティング システム \([!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]、[!INCLUDE[win7](../../../../includes/win7-md.md)] など\) でのみサポートされます。|  
  
 以下の機能はハードウェア アクセラレータによって加速されません。  
  
|機能|説明|  
|--------|--------|  
|印刷されるコンテンツ|印刷されるすべてのコンテンツが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ソフトウェア パイプラインによって表示されます。|  
|<xref:System.Windows.Media.Imaging.RenderTargetBitmap> を使用する、ラスタライズされたコンテンツ|すべてのコンテンツが、<xref:System.Windows.Media.Imaging.RenderTargetBitmap> の <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> メソッドによって描画されます。|  
|<xref:System.Windows.Media.TileBrush> を使用する、並べて表示されるコンテンツ|すべての並べて表示されるコンテンツにおいて <xref:System.Windows.Media.TileBrush> の <xref:System.Windows.Media.TileBrush.TileMode%2A> プロパティが <xref:System.Windows.Media.TileMode> に設定されます。|  
|グラフィックス ハードウェアの最大テクスチャ サイズを超えるサーフェイス。|ほとんどのグラフィックス ハードウェアでは、大型のサーフェイスのサイズは 2048 x 2048 ピクセルまたは 4096 x 4096 ピクセルです。|  
|必要なビデオ RAM 容量がグラフィックス ハードウェアのメモリ容量を上回るすべての操作|Windows SDK の [WPF Performance Suite](../Topic/WPF%20Performance%20Suite.md) に付属する Perforator ツールを使用して、アプリケーション ビデオ RAM の使用量を監視できます。|  
|レイヤード ウィンドウ|レイヤード ウィンドウを使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションで、コンテンツを四角形以外のウィンドウの画面に描画できます。  Windows Display Driver Model \(WDDM\) をサポートするオペレーティング システム \([!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]、[!INCLUDE[win7](../../../../includes/win7-md.md)] など\) では、レイヤード ウィンドウはハードウェア アクセラレータによって加速されます。  [!INCLUDE[winxp](../../../../includes/winxp-md.md)] などのその他のシステムでは、レイヤード ウィンドウはハードウェア アクセラレータを使用せずにソフトウェアで描画されます。<br /><br /> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でレイヤード ウィンドウを有効にするには、<xref:System.Windows.Window> の次のプロパティを設定します。<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> \= <xref:System.Windows.WindowStyle><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> \= `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> \= <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## その他のリソース  
 次の技術情報は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのパフォーマンス特性の分析に役立ちます。  
  
### グラフィックス レンダリングのレジストリ設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のレンダリングを制御するために 4 つのレジストリ設定が用意されています。  
  
|設定|Description|  
|--------|-----------------|  
|**Disable Hardware Acceleration Option**|ハードウェア アクセラレータを有効にするかどうかを指定します。|  
|**Maximum Multisample Value**|[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] コンテンツのアンチエイリアシングのマルチサンプリングの度合いを指定します。|  
|**Required Video Driver Date Setting**|2004 年 11 月より前にリリースされたドライバーに対してハードウェア アクセラレータをシステムで無効にするかどうかを指定します。|  
|**Use Reference Rasterizer Option**|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でリファレンス ラスタライザーを使用するかどうかを指定します。|  
  
 これらの設定には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レジストリ設定の参照方法を認識している外部構成ユーティリティを使用してアクセスできます。  また、これらの設定は、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] レジストリ エディターを使用して値に直接アクセスして作成または変更することもできます。  詳細については、「[グラフィックス レンダリングのレジストリ設定](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md)」を参照してください。  
  
### WPF パフォーマンス プロファイリング ツール  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、アプリケーションの実行時の動作を分析したり、適用可能なパフォーマンス最適化の種類を決定できるパフォーマンス プロファイリング ツール スイートを提供します。  [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] ツール \(WPF Performance Suite\) に含まれるパフォーマンス プロファイリング ツールを次の表に示します。  
  
|ツール|Description|  
|---------|-----------------|  
|Perforator|レンダリング動作の分析に使用します。|  
|ビジュアル プロファイラー|ビジュアル ツリーの要素による [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] サービス \(レイアウトやイベント処理など\) の使用状況に関するプロファイリングで使用します。|  
  
 WPF Performance Suite では、パフォーマンス データを多彩なグラフィカル ビューで表示できます。  WPF のパフォーマンス ツールの詳細については、「[WPF Performance Suite](../Topic/WPF%20Performance%20Suite.md)」を参照してください。  
  
### DirectX 診断ツール  
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 診断ツール \(Dxdiag.exe\) は、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 関連の問題のトラブルシューティングを支援します。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 診断ツールの既定のインストール フォルダーは次のとおりです。  
  
 `~\Windows\System32`  
  
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 診断ツールを実行すると、メイン ウィンドウに一連のタブが表示され、これらのタブを使用して [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 関連の情報を表示および診断することができます。  たとえば、\[システム\] タブにはコンピューターに関するシステム情報が表示され、コンピューターにインストールされている [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] のバージョンが示されます。  
  
 ![スクリーンショット: DirectX 診断ツール](../../../../docs/framework/wpf/advanced/media/directxdiagnostictool-01.png "DirectXDiagnosticTool\_01")  
DirectX 診断ツールのメイン ウィンドウ  
  
## 参照  
 <xref:System.Windows.Media.RenderCapability>   
 <xref:System.Windows.Media.RenderOptions>   
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [WPF Performance Suite](../Topic/WPF%20Performance%20Suite.md)   
 [グラフィックス レンダリングのレジストリ設定](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md)   
 [アニメーションのヒントとテクニック](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)