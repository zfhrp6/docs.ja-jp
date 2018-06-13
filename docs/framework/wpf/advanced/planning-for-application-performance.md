---
title: アプリケーション パフォーマンスの計画
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
ms.openlocfilehash: c8e763686b30ca9c8e1dc5a7f6234d77201e4cba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546953"
---
# <a name="planning-for-application-performance"></a>アプリケーション パフォーマンスの計画
パフォーマンスの目標を達成できるは、どの程度する戦略を作成するパフォーマンスによって異なります。 計画は、任意の製品の開発の最初のステージです。 このトピックでは、良好なパフォーマンスの戦略を開発するためのいくつかの非常に単純な規則について説明します。  
  
## <a name="think-in-terms-of-scenarios"></a>シナリオの観点から考える  
 シナリオを使用するアプリケーションの重要なコンポーネントに注目します。 シナリオは、一般に、お客様、および競合製品から派生します。 常に、お客様を調査し、どのような楽しいに興奮しており、製品、および競合他社製品を調べる。 お客様のフィードバックは、アプリケーションの主要なシナリオを決定するのに役立ちます。 たとえば、起動時に使用されるコンポーネントをデザインする場合は、可能性の高いアプリケーションの起動時に、コンポーネントを 1 回だけ呼び出すことです。 起動時に、主要なシナリオになります。 主要なシナリオの他の例には、目的のフレーム レート、アニメーション シーケンスと、最大作業アプリケーションのセットが可能性があります。  
  
## <a name="define-goals"></a>目標を定義します。  
 目標を使用して、アプリケーションのパフォーマンスが高いか低いかどうかを判断するのに役立ちます。 シナリオのすべての目標を定義する必要があります。 定義するすべてのパフォーマンスの目標は、顧客が期待に基づいている必要があります。 アプリケーションの開発の早い段階で目標順番に表示する、まだ多くの未解決の問題がある場合にセットのパフォーマンスが困難な場合があります。 ただし、初期の目標を設定およびしないより目標に後でそれを変更することをお勧めします。  
  
## <a name="understand-your-platform"></a>プラットフォームを理解します。  
 測定、調査、アプリケーションの開発サイクル中に再設定/修正のサイクルを常に維持します。 開発サイクルの終わりに、最初から、信頼性の高い安定した環境でアプリケーションのパフォーマンスを測定する必要があります。 外部の要因によって変動を避ける必要があります。 たとえば、パフォーマンスをテストするときにウイルス対策ソフトウェアや SMS などの任意の自動更新を無効にする、パフォーマンスに影響しないようにの順序でテスト結果必要があります。 アプリケーションのパフォーマンスを測定するしたら、最大の機能強化の原因となる変更を識別します。 アプリケーションを変更した後は、もう一度、サイクルを開始します。  
  
## <a name="make-performance-tuning-an-iterative-process"></a>パフォーマンス チューニングを反復処理  
 使用して各機能の相対的なコストを把握する必要があります。 たとえば、Microsoft .NET Framework でリフレクションを使用は通常、パフォーマンス、コンピューティング リソースの観点から処理を要する、慎重に使用するためです。 ありません、リフレクションの使用を避けるためにのみ必要がある、アプリケーションのパフォーマンス要件を使用する機能のパフォーマンスに対する要求とのバランスをとるように注意してくださかった。  
  
## <a name="build-towards-graphical-richness"></a>豊かなグラフィックスを作り上げてください。  
 キーの手法を実現するスケーラブルなアプローチを作成するため[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]豊かなグラフィックスと複雑さを作り上げてには、アプリケーションのパフォーマンスです。 常に最低のパフォーマンス負荷の高いリソースを使用して、シナリオの目標を達成すると開始します。 これらの目標を達成すると、機能を使用して複数のパフォーマンス負荷の高い常にシナリオの目標を念頭を豊かなグラフィックス ビルドします。 ただし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]非常に豊富なプラットフォームは、非常に多彩なグラフィック機能を提供します。 考えずパフォーマンス負荷の高い機能を使用すると、アプリケーション全体のパフォーマンスに悪影響を与えることができます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールは、広く使用されているカスタマイズの場合、コントロールの動作を変更しない中に、表示されるようにすることでは本質的に拡張できます。 活用してスタイル、データ テンプレート、およびコントロール テンプレートを作成し、カスタマイズ可能な増分進化[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]パフォーマンス要件に適合します。  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [[テキスト]](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
