---
title: "アプリケーション パフォーマンスの計画 | Microsoft Docs"
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
  - "アプリケーション, 最適化"
  - "WPF アプリケーション, 最適化"
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# アプリケーション パフォーマンスの計画
パフォーマンスの目標を達成できるかどうかは、適切なパフォーマンス計画を立てられるかどうかにかかっています。  すべての製品の開発は計画から始まります。  このトピックでは、適切なパフォーマンス計画を立てるためのごく簡単なルールをいくつか紹介します。  
  
## シナリオの観点から考える  
 シナリオを利用して、アプリケーションの重要なコンポーネントに的を絞ることができます。  シナリオは、顧客や競合製品から導き出されるのが一般的です。  常に顧客をよく観察し、顧客が自分たちの製品や競合他社の製品のどこに引き付けられているのかを解明します。  顧客のフィードバックは、アプリケーションの主要なシナリオを特定するうえで役に立ちます。  たとえば、起動時に使用されるコンポーネントを設計している場合は、そのコンポーネントが呼び出されるのは一般にアプリケーションの起動時の 1 回だけであるため、  起動時間がキー シナリオになります。  そのほか、一連のアニメーションの目的のフレーム レートや、アプリケーションの最大作業セットなどがキー シナリオになる場合もあります。  
  
## 目標を定義する  
 目標は、アプリケーションのパフォーマンスが高いか低いかの判断に役立ちます。  すべてのシナリオで目標を定義する必要があります。  パフォーマンスの目標はすべて、顧客の期待に基づいて定義します。  アプリケーション開発サイクルの早い段階では未解決の問題もまだ多く、パフォーマンスの目標を設定するのが困難な場合もあります。  しかし、まったく目標を設定しないよりは、初期目標を設定してそれを後から修正する方が良いと言えます。  
  
## プラットフォームを理解する  
 アプリケーション開発サイクルでは、測定、調査、改良\/修正というサイクルを常に維持します。  開発サイクルの始めから終わりまで、信頼できる安定した環境でアプリケーションのパフォーマンスを測定する必要があります。  外部要因による変動は避けるようにしてください。  たとえば、パフォーマンスをテストするときには、ウイルス対策ソフトウェアや自動更新 \(SMS など\) を無効にして、それらがパフォーマンス テストの結果に影響しないようにする必要があります。  アプリケーションのパフォーマンスの測定が完了したら、最大の効果を得るにはどこを変更すればよいのかを特定します。  アプリケーションに変更を加えた後、再び同じサイクルを開始します。  
  
## パフォーマンス チューニングを反復プロセスにする  
 使用する各機能の相対負荷を知る必要があります。  たとえば、[!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] のリフレクションを使用すると、一般にコンピューティング リソースの面でパフォーマンスへの影響が大きくなります。したがって、この機能は適切な判断に基づいて使用する必要があります。  リフレクションを使用しないようにするということではありません。ただ、アプリケーションのパフォーマンスの要件と、使用する機能のパフォーマンスへの影響とのバランスに注意する必要があるということです。  
  
## 豊かなグラフィックスを目指す  
 スケーラブルなアプローチで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのパフォーマンスの目標を達成するための主な手法の 1 つとして、豊かで複雑なグラフィックスを目指します。  最初は常に、パフォーマンスへの影響が最も少ないリソースを使用してシナリオの目標を達成します。  それらの目標を達成できたら、今度は、パフォーマンスへの影響が大きい機能を使用して豊かなグラフィックスを目指します。シナリオの目標は常に念頭に置いておきます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] はきわめて機能豊富なプラットフォームであり、多彩なグラフィックス機能が用意されています。  パフォーマンスへの影響が大きい機能を何も考えずに使用すると、アプリケーション全体のパフォーマンスが低下する可能性があります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールは本質的に拡張性が高く、コントロールの動作を変えずに外観を広範にカスタマイズすることができます。  スタイル、データ テンプレート、およびコントロール テンプレートを活用することにより、パフォーマンスの要件に対応したカスタマイズ可能な[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を作成し、徐々に発展させていくことができます。  
  
## 参照  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [テキスト](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)