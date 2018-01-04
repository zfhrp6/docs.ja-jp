---
title: "スタイラスからの入力のインターセプト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5fde62e2e1ab17b26c91051f68b7d4225450c60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="intercepting-input-from-the-stylus"></a>スタイラスからの入力のインターセプト
<xref:System.Windows.Input.StylusPlugIns>アーキテクチャ上の低レベルの制御を実装するためのメカニズムを提供する<xref:System.Windows.Input.Stylus>入力し、デジタル インクの作成<xref:System.Windows.Ink.Stroke>オブジェクト。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラスには、カスタム動作を実装し、最適なパフォーマンスのスタイラス デバイスからのデータのストリームに適用するメカニズムが用意されています。  
  
 このトピックは、次の内容で構成されています。  
  
-   [アーキテクチャ](#Architecture)  
  
-   [スタイラス プラグインを実装します。](#ImplementingStylusPlugins)  
  
-   [InkCanvas へのプラグインの追加](#AddingYourPluginToAnInkCanvas)  
  
-   [まとめ](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>アーキテクチャ  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>の進化は、 [StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409)で説明する、Api[へのアクセスと操作のペン入力](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)で、 [Microsoft Windows XP Tablet PC Edition ソフトウェア開発キット 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)です。  
  
 各<xref:System.Windows.UIElement>が、<xref:System.Windows.UIElement.StylusPlugIns%2A>であるプロパティ、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>です。 追加することができます、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>要素の<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティを操作する<xref:System.Windows.Input.StylusPoint>データを生成します。 <xref:System.Windows.Input.StylusPoint>データを含む、システムのデジタイザーでサポートされているすべてのプロパティから成る、<xref:System.Windows.Input.StylusPoint.X%2A>と<xref:System.Windows.Input.StylusPoint.Y%2A>、データをポイントだけでなく<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>データ。  
  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>オブジェクトは、データの発生元のストリームに直接挿入、<xref:System.Windows.Input.Stylus>デバイスを追加すると、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>を<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティです。 プラグインを追加する順序、<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクションが表示される順序を決定する<xref:System.Windows.Input.StylusPoint>データ。 たとえば、特定の地域への入力を制限するフィルター プラグインを追加して記述されているジェスチャを認識するプラグインを追加して、ジェスチャを認識するプラグインを受け取りますフィルター選択された<xref:System.Windows.Input.StylusPoint>データ。  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>スタイラス プラグインを実装します。  
 プラグインを実装するには、派生クラスを<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>です。 このクラスはデータのストリームにあるため、<xref:System.Windows.Input.Stylus>です。 このクラスでは、値を変更することができます、<xref:System.Windows.Input.StylusPoint>データ。  
  
> [!CAUTION]
>  場合、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>をスローするか、閉じる、アプリケーションは、例外が発生します。 使用するコントロールを十分にテストする必要があります、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>のみがわかっている場合に、コントロールを使用して、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>例外はスローされません。  
  
 次の例で変更することにより、スタイラス入力を制限するプラグイン、<xref:System.Windows.Input.StylusPoint.X%2A>と<xref:System.Windows.Input.StylusPoint.Y%2A>の値が、<xref:System.Windows.Input.StylusPoint>からデータを受信、<xref:System.Windows.Input.Stylus>デバイス。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>InkCanvas へのプラグインの追加  
 カスタム プラグインを使用する最も簡単 InkCanvas から派生するクラスを実装し、追加するには、<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティです。  
  
 次の例では、カスタム<xref:System.Windows.Controls.InkCanvas>インクをフィルター処理します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 追加する場合、`FilterInkCanvas`をアプリケーションと実行、わかりますインクではないことまでの領域に制限されているユーザーがストロークを完了後します。 これは、ため、<xref:System.Windows.Controls.InkCanvas>が、<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>プロパティとは、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>のメンバーであると、<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクション。 カスタム<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>に追加する、<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクションには、<xref:System.Windows.Input.StylusPoint>の後にデータ<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>データを受信します。 その結果、<xref:System.Windows.Input.StylusPoint>データはフィルターされませんまで、ユーザーがストロークを終了するペンを持ち上げる後です。 ユーザーが描画には、インクをフィルターするに挿入する必要があります、`FilterPlugin`する前に、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>です。  
  
 次の c# コードに示しますカスタム<xref:System.Windows.Controls.InkCanvas>描画されると、インクをフィルター処理します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>まとめ  
 独自の派生によって<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラスとそれらに挿入する<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>コレクション、デジタル インクの動作が大幅に向上することができます。 アクセスがある、<xref:System.Windows.Input.StylusPoint>データを生成するをカスタマイズする機会を提供するので、<xref:System.Windows.Input.Stylus>入力します。 このような低レベルのアクセス権があるため、<xref:System.Windows.Input.StylusPoint>データ、アプリケーションのインクの収集と最適なパフォーマンスでレンダリングを実装することができます。  
  
## <a name="see-also"></a>参照  
 [高度なインク処理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [アクセスとペン入力を操作します。](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
