---
title: "パフォーマンスの最適化 : ハードウェアの活用 | Microsoft Docs"
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
  - "ハードウェア レンダリング パイプライン"
  - "描画層"
  - "ソフトウェア レンダリング パイプライン"
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# パフォーマンスの最適化 : ハードウェアの活用
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の内部アーキテクチャには、ハードウェアとソフトウェアの 2 つのレンダリング パイプラインがあります。  このトピックでは、レンダリング パイプラインに関して、アプリケーションのパフォーマンスの最適化に関する判断に役立つ情報を提供します。  
  
## ハードウェア レンダリング パイプライン  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のパフォーマンスを決定する最も重要な要因の 1 つは、それがレンダリング制約であるということです。つまり、描画するピクセルが増えるほどパフォーマンスへの負荷が大きくなります。  ただし、[!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)] にオフロードできるレンダリングが増えれば、その分パフォーマンスが向上します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのハードウェア レンダリング パイプラインは、[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] Version 7.0 以上をサポートするハードウェアの [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] 機能を最大限に活用します。  [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] Version 7.0 と PixelShader 2.0\+ の機能をサポートするハードウェアでは、さらなる最適化を実現できます。  
  
## ソフトウェア レンダリング パイプライン  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のソフトウェア レンダリング パイプラインは完全に CPU 制約です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、CPU の SSE\/SSE2 命令セットを活用して、最適化されたフル機能のソフトウェア ラスタライザーを実装します。  ハードウェア レンダリング パイプラインを使用して実行できないアプリケーション機能のレンダリングは、シームレスにソフトウェア レンダリングに戻ります。  
  
 ソフトウェア モードでのレンダリングにおけるパフォーマンスの最大の問題は、塗りつぶし速度に関連する問題です。塗りつぶし速度は、描画するピクセルの数として定義されます。  ソフトウェア レンダリング モードでのパフォーマンスに懸念がある場合は、ピクセルの再描画の回数をできるだけ減らすようにしてください。  たとえば、アプリケーションに青い背景があり、その上にやや透明のイメージを描画する場合は、アプリケーションのすべてのピクセルが 2 回描画されることになります。  その結果、アプリケーションにイメージが含まれている場合は、青い背景のみの場合に比べて描画に 2 倍の時間がかかることになります。  
  
### グラフィックスの描画層  
 アプリケーションが実行されるハードウェア構成を予測するのは非常に難しい場合があります。  ただし、異なるハードウェアで実行された場合にシームレスに機能を切り替えられるようにアプリケーションを設計することもできます。これにより、アプリケーションでそれぞれのハードウェア構成を最大限に活用できます。  
  
 そのために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にはシステムのグラフィックス機能を実行時に判別する機能が用意されています。  グラフィックス機能の判別は、ビデオ カードを 3 つの描画層に分類することによって行われます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が公開する [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] を使用して描画層を照会することにより、  アプリケーションは、ハードウェアでサポートされている描画層に応じて、実行時に異なるコード パスを受け取ることができます。  
  
 描画層のレベルに大きく影響するグラフィックス ハードウェアの機能は、次のとおりです。  
  
-   **ビデオ RAM** グラフィックス ハードウェアのビデオ メモリの量によって、グラフィックスを合成する際に使用できるバッファーのサイズと数が決まります。  
  
-   **ピクセル シェーダー** ピクセル シェーダーは、ピクセル単位で効果を計算するグラフィックス処理関数です。  表示するグラフィックスの解像度によっては、各表示フレームの処理に数百万ピクセルが必要な場合もあります。  
  
-   **頂点シェーダー** 頂点シェーダーは、オブジェクトの頂点データの算術演算を実行するグラフィックス処理関数です。  
  
-   **マルチテクスチャのサポート** マルチテクスチャがサポートされていると、3D グラフィックス オブジェクトのブレンド操作を行うときに、2 つ以上の別個のテクスチャを適用できます。  マルチテクスチャのサポートの度合いは、グラフィックス ハードウェアのマルチテクスチャ ユニットの数によって決まります。  
  
 ピクセル シェーダー、頂点シェーダー、およびマルチテクスチャの各機能を使用して、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] の特定のバージョン レベルを定義し、次にこのバージョン レベルを使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のさまざまな描画層を定義します。  
  
 グラフィックス ハードウェアの機能によって、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの表示能力が決まります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] システムは、次の 3 つの描画階層を定義します。  
  
-   **描画層 0** グラフィックス ハードウェアの加速が使用されません。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] のバージョン レベルは Version 7.0 未満です。  
  
-   **描画層 1** グラフィックス ハードウェアの加速が部分的に使用されます。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] のバージョン レベルは、Version 7.0 以上で Version 9.0 未満です。  
  
-   **描画層 2** ほとんどのグラフィックス機能でグラフィックス ハードウェアの加速を使用します。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] のバージョン レベルは Version 9.0 以上です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レンダリング層の詳細については、「[グラフィックスの描画層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)」を参照してください。  
  
## 参照  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [テキスト](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)