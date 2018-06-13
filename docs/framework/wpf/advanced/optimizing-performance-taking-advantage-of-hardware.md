---
title: 'パフォーマンスの最適化 : ハードウェアの活用'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: eb790da63b4636e3dd6c25ea118075304702acc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547255"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>パフォーマンスの最適化 : ハードウェアの活用
内部アーキテクチャ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、2 つのレンダリング パイプライン、ハードウェアおよびソフトウェア。 このトピックをアプリケーションのパフォーマンスの最適化に関する決定を行うには、これらのレンダリング パイプラインについて情報を提供します。  
  
## <a name="hardware-rendering-pipeline"></a>ハードウェア レンダリング パイプライン  
 判断する最も重要な要因の 1 つ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]パフォーマンスが表示範囲であること、ピクセルの数が大きいほど、パフォーマンス コストをレンダリングする必要があります。 ただし、できるレンダリングにオフロードできます、 [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)]、複数のパフォーマンス向上することができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション ハードウェア レンダリング パイプラインを最大限の活用[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]の最小値をサポートするハードウェアで機能[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]バージョン 7.0。 さらに最適化することによって得をサポートするハードウェア[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]バージョン 7.0 と PixelShader 2.0 + 機能します。  
  
## <a name="software-rendering-pipeline"></a>ソフトウェア レンダリング パイプライン  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ソフトウェア レンダリング パイプラインは完全に CPU バインドします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sse 命令と SSE2 命令の利用を最適化された、完全な機能を備えたソフトウェア ラスタライザーを実装する、CPU で設定します。 ソフトウェアへのフォールバックは、シームレス ハードウェア レンダリング パイプラインを使用してアプリケーションの機能を表示することはできません。  
  
 最大のパフォーマンスの問題が発生フィル レートで表示するにはピクセルの数として定義されているに関連するソフトウェアのモードでのレンダリング時にします。 ソフトウェア レンダリング モードでのパフォーマンスに関する懸念がある場合は、ピクセルが再描画される回数を超えるを最小限に抑えてください。 たとえば、上にわずかに透明のイメージを表示し、青色の背景を持つアプリケーションがある場合は、すべてのアプリケーションを 2 回のピクセルがレンダリングされます。 その結果はかかる 2 回の背景色を青にした場合よりも、イメージを使用してアプリケーションを表示するためにします。  
  
### <a name="graphics-rendering-tiers"></a>グラフィックスの描画層  
 アプリケーションを実行するハードウェア構成を予測する非常に困難な場合があります。 ただし、設計により、アプリケーションにシームレスに切り替える機能別のハードウェアで実行されているときにそれぞれ別のハードウェア構成を最大限に活用がかかることができるようにすることができます。  
  
 これを実現する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]実行時にシステムのグラフィックス機能を判断する機能を提供します。 グラフィックス機能は、3 つの描画層の 1 つとして、ビデオ カードを分類することによって決定されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 公開、[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]アプリケーション描画機能層をクエリすることができます。 アプリケーションは、ハードウェアでサポートされている描画層によって実行時に別のコード パスを受け取ることができます。  
  
 描画層に最も影響を与えるグラフィックス ハードウェアの機能:  
  
-   **ビデオ RAM** グラフィックス ハードウェアのビデオ メモリの量で、グラフィックスの構築に利用できるバッファーのサイズと数が決まります。  
  
-   **ピクセル シェーダー** ピクセル シェーダーは、ピクセル単位で効果を計算するグラフィックス処理機能です。 表示されるグラフィックスの解像度によっては、各表示フレームの処理に数百万単位のピクセルが必要になることがあります。  
  
-   **頂点シェーダー** 頂点シェーダーは、オブジェクトの頂点データに数学演算を実行するグラフィックス処理機能です。  
  
-   **マルチテクスチャ サポート** マルチテクスチャ サポートとは、3D グラフィックス オブジェクトにブレンド操作を実行するとき、2 つ以上の異なるテクスチャを適用できる機能のことです。 マルチテクスチャ サポートの度合いは、グラフィックス ハードウェア上のマルチテクスチャ ユニットの数で決まります。  
  
 ピクセル シェーダー、頂点シェーダーとマルチ テクスチャ機能の定義に使用特定[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]さらに、さまざまな表示の層の定義に使用されるバージョン レベル[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  
  
 グラフィックス ハードウェアの機能により [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのレンダリング能力が決まります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] システムには次の 3 つの描画層があります。  
  
-   **描画層 0** グラフィックス ハードウェアの高速化はありません。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]バージョン レベルがバージョン 7.0 未満です。  
  
-   **階層 1 のレンダリング**部分のグラフィックス ハードウェア アクセラレータです。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]バージョン レベルには、バージョン 7.0 では、以下と**いずれか小さいほう**9.0 のバージョンよりもします。  
  
-   **描画層 2** ほとんどのグラフィックス機能でグラフィックス ハードウェア高速が利用されます。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] バージョンのレベルはバージョン 9.0 以上です。  
  
 詳細については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]階層を表示するを参照してください[グラフィックスの描画層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [[テキスト]](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
