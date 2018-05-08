---
title: Freezable オブジェクトの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: d3b9f6f7af22b2a846f4ee34e8d4d00bb032fd69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="freezable-objects-overview"></a>Freezable オブジェクトの概要
このトピックを効果的に使用して作成する方法について説明<xref:System.Windows.Freezable>オブジェクトで、アプリケーションのパフォーマンスを改善する特別な機能を提供します。 Freezable オブジェクトの例には、ブラシ、ペン、変換、ジオメトリ、およびアニメーションが含まれます。  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Freezable は何ですか。  
 A<xref:System.Windows.Freezable>を 2 つの状態を持つオブジェクトの特別な種類: 固定おらず、固定されています。 マスクされていない、ときに、<xref:System.Windows.Freezable>するその他のオブジェクトと同様に動作が表示されます。 固定されると、<xref:System.Windows.Freezable>変更不要になったことができます。  
  
 A<xref:System.Windows.Freezable>提供、<xref:System.Windows.Freezable.Changed>オブジェクトに変更を加えるのオブザーバーに通知するイベントです。 固定すること、<xref:System.Windows.Freezable>変更通知にリソースを費やす必要がなくなったため、パフォーマンスを向上することができます。 固定された<xref:System.Windows.Freezable>、固定されていないときに、スレッド間で共有することも<xref:System.Windows.Freezable>ことはできません。  
  
 <xref:System.Windows.Freezable>クラスには多くのアプリケーションで最も<xref:System.Windows.Freezable>オブジェクト[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グラフィックス サブシステムに関連します。  
  
 <xref:System.Windows.Freezable>クラスは、特定のグラフィックス システム オブジェクトを使用するが容易し、アプリケーションのパフォーマンスを向上させることができます。 継承する型の例については<xref:System.Windows.Freezable>含める、 <xref:System.Windows.Media.Brush>、 <xref:System.Windows.Media.Transform>、および<xref:System.Windows.Media.Geometry>クラスです。 アンマネージ リソースを含んでいるため、システムがこれらのオブジェクトの変更を監視を更新した後、元のオブジェクトへの変更がある場合に、対応するアンマネージ リソースを更新する必要があります。 場合でも、実際には、グラフィックス システム オブジェクトを変更しない、システム使う必要がありますが、オブジェクトの監視にリソースの一部これを変更する場合にします。  
  
 たとえば、作成する、<xref:System.Windows.Media.SolidColorBrush>ブラシし、ボタンの背景の描画に使用します。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 ボタンが表示されると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]グラフィックス サブ システム ボタンの外観を作成するピクセルのグループを描画する提供情報を使用します。 純色のブラシを使用して、ボタンを描画する方法について説明した、純色のブラシしない描画を行う実際には。 グラフィックス システムが、ボタンとブラシに高速で低レベルのオブジェクトを生成し、実際に画面に表示されるこれらのオブジェクトはします。  
  
 ブラシを変更する場合は、それらの低レベルのオブジェクトが再生成する必要があります。 Freezable クラスは、どのようなことができます、ブラシが変更されたときに更新して、対応する生成され、低レベルのオブジェクトを検索します。 この機能を有効にすると、ブラシが「固定」すると言います。  
  
 フリーズの<xref:System.Windows.Freezable.Freeze%2A>メソッドでは、この自動更新機能を無効にすることができます。 このメソッドを使用すると、「固定」、または不可能な状態になるブラシを作成します。  
  
> [!NOTE]
>  Freezable オブジェクトすべてを固定することができます。 スローされないようにする、 <xref:System.InvalidOperationException>、Freezable オブジェクトの値をチェックして<xref:System.Windows.Freezable.CanFreeze%2A>固定にする前に固定できるかどうかを決定するプロパティです。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 不要になった、フリーズを修正する必要がある場合は、パフォーマンス上の利点を提供固定します。 この例では、ブラシを固定する場合は、グラフィックス システムは変更を監視する必要がなくなります。 グラフィックス システムは、その他の最適化をブラシが変更されないに認識していることもできます。  
  
> [!NOTE]
>  便宜上、freezable オブジェクトは、明示的に固定する場合を除き、固定されていない残ります。  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Freezable の使用  
 使用、固定されていない freezable は、その他の種類のオブジェクトを使用するなどです。 次の例では、色、<xref:System.Windows.Media.SolidColorBrush>が黄色から赤に後に変更ボタンの背景の描画に使用されます。 グラフィックス システムでは、バック グラウンドで自動的に変更するボタン黄色から赤に画面の [次へ] の更新では動作します。  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Freezable はフリーズ  
 させる、<xref:System.Windows.Freezable>呼び出して、変更不可能になってその<xref:System.Windows.Freezable.Freeze%2A>メソッドです。 Freezable オブジェクトを格納しているオブジェクトを固定すると、それらのオブジェクトが固定されているとします。 保持する場合など、<xref:System.Windows.Media.PathGeometry>図形やが含まれているセグメントは固定すぎます。  
  
 Freezable**できません**次のいずれかに当てはまる場合に固定します。  
  
-   アニメーション化されたか、データ バインドされたプロパティ。  
  
-   動的リソースによって設定されるプロパティがあります。 (を参照してください、 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)動的なリソースの詳細についてはします)。  
  
-   含まれている<xref:System.Windows.Freezable>サブオブジェクトを固定することはできません。  
  
 これらの条件が false の場合、および変更にしないかどうか、 <xref:System.Windows.Freezable>、その前に説明したパフォーマンス メリットを得られることを固定する必要があります。  
  
 呼び出す、freezable の<xref:System.Windows.Freezable.Freeze%2A>メソッドを変更できません。 固定された変更しようとしています。 オブジェクトの原因として、<xref:System.InvalidOperationException>がスローされます。 次のコードでは、フリーズした後にブラシを変更するために、例外がスローされます。  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 この例外がスローされることを避けるためには、使用することができます、<xref:System.Windows.Freezable.IsFrozen%2A>メソッドを呼び出せば確認するかどうか、<xref:System.Windows.Freezable>が固定されています。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 前のコード例では、変更可能なコピーが行われたの固定されたオブジェクトを使用して、<xref:System.Windows.Freezable.Clone%2A>メソッドです。 次のセクションでは、さらに詳しくクローン作成について説明します。  
  
 **注**ため固定された freezable できませんアニメーション化、アニメーションは自動的に作成の変更可能な複製固定された<xref:System.Windows.Freezable>オブジェクトをアニメーション化をしようとすると、<xref:System.Windows.Media.Animation.Storyboard>です。 によるパフォーマンスのオーバーヘッドが複製をなくすためには、アニメーション化する場合にマスクされていないオブジェクトのままにします。 ストーリー ボードでのアニメーション化の詳細については、次を参照してください。、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。  
  
### <a name="freezing-from-markup"></a>マークアップからのフリーズ  
 固定するのには、<xref:System.Windows.Freezable>オブジェクトを使用するマークアップで宣言された、`PresentationOptions:Freeze`属性。 次の例で、<xref:System.Windows.Media.SolidColorBrush>はページ リソースとして宣言されており、固定されています。 ボタンの背景を設定するのには使用されます。  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 使用する、`Freeze`属性、プレゼンテーションのオプションの名前空間にマップする必要があります:`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`です。 `PresentationOptions` この名前空間のマッピングの推奨されるプレフィックスを示します。  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 すべての XAML リーダーは、この属性を認識、ためにを使用することをお勧めしますが、 [mc: Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)をマークする、`Presentation:Freeze`属性を無視できます。  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 詳細については、次を参照してください。、 [mc: Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)ページ。  
  
### <a name="unfreezing-a-freezable"></a>「固定解除」フリーズ  
 1 回凍結されている場合、<xref:System.Windows.Freezable>決してを変更または固定です。 ただし、を使用して、固定されていない複製を作成することができます、<xref:System.Windows.Freezable.Clone%2A>または<xref:System.Windows.Freezable.CloneCurrentValue%2A>メソッドです。  
  
 次の例では、ブラシを使用してボタンの背景が設定され、そのブラシは、固定されています。 ブラシを使用して、固定されていないコピーされる、<xref:System.Windows.Freezable.Clone%2A>メソッドです。 クローンが変更し、赤、黄色からボタンの背景を変更するために使用します。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  アニメーションを決してを新しいコピーを使用するどの複製方法に関係なく<xref:System.Windows.Freezable>です。  
  
 <xref:System.Windows.Freezable.Clone%2A>と<xref:System.Windows.Freezable.CloneCurrentValue%2A>メソッドが、freezable のディープ コピーを作成します。 場合は、格納されているその他の固定 freezable オブジェクトも複製され変更可能です。 たとえば、固定された複製する<xref:System.Windows.Media.PathGeometry>を変更可能なため、図とが含まれているセグメントもコピーされ変更可能です。  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Freezable クラスの作成  
 派生したクラス<xref:System.Windows.Freezable>次の機能を取得します。  
  
-   特殊な状態: 読み取り専用 (固定)、書き込み可能な状態です。  
  
-   スレッド セーフ: 固定された<xref:System.Windows.Freezable>スレッド間で共有できます。  
  
-   変更通知の詳細: その他のとは異なり<xref:System.Windows.DependencyObject>s、Freezable オブジェクトでは、変更通知サブ プロパティの値を変更します。  
  
-   簡単な複製: Freezable のクラスが既にディープ クローンを生成するいくつかのメソッドを実装します。  
  
 A<xref:System.Windows.Freezable>の種類は、 <xref:System.Windows.DependencyObject>、ため、依存関係プロパティ システムを使用します。 クラスのプロパティの依存関係プロパティを指定する必要はありませんが、依存関係プロパティを使用する必要のあるコードを記述するための量を削減は、<xref:System.Windows.Freezable>注意の依存関係プロパティをクラスが設計されています。 依存関係プロパティ システムの詳細については、次を参照してください。、[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)です。  
  
 各<xref:System.Windows.Freezable>サブクラスをオーバーライドする必要があります、<xref:System.Windows.Freezable.CreateInstanceCore%2A>メソッドです。 クラスは、そのすべてのデータの依存関係プロパティを使用している場合は、作業が終了します。  
  
 クラスに依存関係のないプロパティのデータ メンバーが含まれている場合も、次のメソッドをオーバーライドする必要があります。  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 次のルールにアクセスして、依存関係プロパティではないデータ メンバーへの書き込みを確認する必要がも。  
  
-   いずれかの先頭に[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]依存関係のないプロパティのデータ メンバーを読み取る、呼び出し、<xref:System.Windows.Freezable.ReadPreamble%2A>メソッドです。  
  
-   依存関係のないプロパティのデータ メンバーの書き込みをすべての API の先頭には、呼び出し、<xref:System.Windows.Freezable.WritePreamble%2A>メソッドです。 (呼び出した後<xref:System.Windows.Freezable.WritePreamble%2A>で、 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]、追加の呼び出しを行う必要はありません<xref:System.Windows.Freezable.ReadPreamble%2A>も依存関係のないプロパティのデータ メンバーを読み取るかどうかです)。  
  
-   呼び出す、<xref:System.Windows.Freezable.WritePostscript%2A>依存関係のないプロパティのデータ メンバーへの書き込みメソッドを終了する前にメソッドです。  
  
 クラスにある非依存関係プロパティのデータ メンバーが含まれて かどうか<xref:System.Windows.DependencyObject>オブジェクトも呼び出す必要があります、<xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A>メソッド メンバーを設定している場合でもでは、これらの値、変更のするたびに`null`です。  
  
> [!NOTE]
>  各を開始することが非常に重要<xref:System.Windows.Freezable>呼び出し基本実装をオーバーライドするメソッド。  
  
 カスタムの例については<xref:System.Windows.Freezable>クラスを参照してください、[カスタム アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=159981)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Freezable>  
 [カスタム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=159981)  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
