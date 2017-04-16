---
title: "Freezable オブジェクトの概要 | Microsoft Docs"
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
  - "クラス, Freezable"
  - "Freezable オブジェクト, description"
  - "固定解除 (Freezable オブジェクトを)"
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# Freezable オブジェクトの概要
ここでは、アプリケーションのパフォーマンス向上のための特別な機能を備えた <xref:System.Windows.Freezable> オブジェクトの、効率的な使用方法および作成方法について説明します。  フリーズ可能オブジェクトには、ブラシ、ペン、変換、ジオメトリ、アニメーションなどがあります。  
  
 このトピックは、次のセクションで構成されています。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="whatisafreezable"></a>   
## Freezable \(フリーズ可能\) とは  
 <xref:System.Windows.Freezable> は、非フリーズとフリーズの 2 つの状態を持つ特殊な型のオブジェクトです。  フリーズしていない <xref:System.Windows.Freezable> は、他のオブジェクトと同様に動作しているように見えます。  <xref:System.Windows.Freezable> をフリーズすると、変更できなくなります。  
  
 <xref:System.Windows.Freezable> には、オブジェクトの変更を監視者に通知するための <xref:System.Windows.Freezable.Changed> イベントがあります。  <xref:System.Windows.Freezable> をフリーズすると、変更通知のためのリソースが不要になるので、パフォーマンスが向上します。  また、フリーズされた <xref:System.Windows.Freezable> はスレッド間で共有できますが、フリーズされていない <xref:System.Windows.Freezable> は共有できません。  
  
 <xref:System.Windows.Freezable> クラスはさまざまな目的に使用できますが、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の <xref:System.Windows.Freezable> オブジェクトのほとんどは、グラフィックス サブシステムに関連するものです。  
  
 <xref:System.Windows.Freezable> クラスを使用すると、特定のグラフィックス システムのオブジェクトが使いやすくなり、アプリケーション パフォーマンスを向上させることができます。  <xref:System.Windows.Freezable> から継承するクラスには、<xref:System.Windows.Media.Brush>、<xref:System.Windows.Media.Transform>、<xref:System.Windows.Media.Geometry> などがあります。  このようなクラスにはアンマネージ リソースが格納されているので、システムはオブジェクトが変更されたかどうかを監視する必要があります。元のオブジェクトに変更があった場合は、対応するアンマネージ リソースを更新します。  実際にはグラフィックス システムのオブジェクトが変更されることがなくても、万一の変更に備えて、システムはオブジェクトの監視用にリソースの一部を消費しなければなりません。  
  
 たとえば、<xref:System.Windows.Media.SolidColorBrush> ブラシを作成して、ボタンの背景の塗りつぶしに使用するとします。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 ボタンがレンダリングされるとき、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のグラフィックス サブシステムは指定された情報を使用してピクセルのグループを塗りつぶし、ボタンの外観を作成します。  ボタンの描画方法を示すために単色のブラシを指定したとしても、この単色のブラシが実際に塗りつぶしを行うわけではありません。  グラフィックス システムによって、ボタンおよびブラシの高速かつ低レベルのオブジェクトが生成され、実際に画面に表示されます。  
  
 ブラシに変更を加える場合は、このような低レベルのオブジェクトの再生成が必要です。  Freezable クラスとは、ブラシに、自身に対応する生成済みの低レベル オブジェクトを検出して自身が変更されたときにそのオブジェクトを更新するという能力を与えるものです。  この機能が有効化されているときは、ブラシは "フリーズされていない" といいます。  
  
 フリーズ可能オブジェクトの <xref:System.Windows.Freezable.Freeze%2A> は、この自己更新機能を無効化するためのメソッドです。  このメソッドを使用すると、ブラシを "フリーズ" 状態、つまり変更不可能にすることができます。  
  
> [!NOTE]
>  すべての Freezable オブジェクトをフリーズできるわけではありません。  <xref:System.InvalidOperationException> がスローされることを避けるには、Freezable オブジェクトをフリーズする前に <xref:System.Windows.Freezable.CanFreeze%2A> プロパティの値を調べて、フリーズ可能かどうかを判断します。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 フリーズ可能オブジェクトを変更する必要がなくなった場合は、フリーズすることによってパフォーマンスが向上します。  この例では、ブラシをフリーズすると、グラフィックス システムがブラシの変更を監視する必要はなくなります。  グラフィックス システムはこのブラシが変更されないことを認識しているので、その他の最適化も実行できるようになります。  
  
> [!NOTE]
>  便宜を図るために、フリーズ可能オブジェクトは、明示的にフリーズされない限り非フリーズ状態を維持します。  
  
<a name="frozenfreezables"></a>   
## Freezable の使用  
 フリーズされていないフリーズ可能オブジェクトの使用は、その他の種類のオブジェクトの使用に似ています。  次のコード例では、<xref:System.Windows.Media.SolidColorBrush> の色をボタンの背景塗りつぶしに使用した後で、黄色から赤に変更します。  グラフィックス システムが内部的処理を行い、画面が次回更新されたときにボタンを黄色から赤に自動的に変更します。  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### Freezable のフリーズ  
 <xref:System.Windows.Freezable> を変更不可にするには、その<xref:System.Windows.Freezable.Freeze%2A> メソッドを呼び出します。  フリーズ可能オブジェクトを格納するオブジェクトをフリーズすると、格納されているオブジェクトもフリーズされます。  たとえば、<xref:System.Windows.Media.PathGeometry> をフリーズすると、格納されている数字およびセグメントもフリーズされます。  
  
 次のいずれかに当てはまる場合は、Freezable をフリーズすることはできません。  
  
-   アニメーション化されたプロパティ、またはデータ バインドされたプロパティがある。  
  
-   プロパティが動的リソースによって設定されている   \(動的リソースの詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください\)。  
  
-   <xref:System.Windows.Freezable> に格納されているサブオブジェクトがフリーズ不可能である。  
  
 これらの条件に該当しない場合に、それ以降 <xref:System.Windows.Freezable> を変更しないことが明らかならば、既に説明したように、パフォーマンスを向上させるためにオブジェクトをフリーズしてください。  
  
 フリーズ可能オブジェクトの <xref:System.Windows.Freezable.Freeze%2A> メソッドをいったん呼び出すと、そのオブジェクトは変更できなくなります。  フリーズされたオブジェクトを変更しようとすると、<xref:System.InvalidOperationException> がスローされます。  次のコードでは、ブラシをフリーズした後に変更しようとしているので、例外がスローされます。  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 この例外がスローされるのを避けるには、<xref:System.Windows.Freezable.IsFrozen%2A> メソッドを使用して、<xref:System.Windows.Freezable> がフリーズされているかどうかを判断します。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 前のコード例では、フリーズされたオブジェクトの変更可能なコピーを、<xref:System.Windows.Freezable.Clone%2A> メソッドを使用して作成しました。  複製の詳細については、次のセクションで説明します。  
  
 **メモ** フリーズされたフリーズ可能オブジェクトはアニメーション化できないので、<xref:System.Windows.Media.Animation.Storyboard> を使用してアニメーション化しようとすると、フリーズされた <xref:System.Windows.Freezable> オブジェクトの変更可能な複製がアニメーション システムによって自動的に作成されます。  複製によって生じるパフォーマンス オーバーヘッドを回避するために、オブジェクトをアニメーション化する場合は非フリーズ状態のままにしてください。  ストーリーボードを使用したアニメーションの詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
### マークアップからのフリーズ  
 マークアップで宣言された <xref:System.Windows.Freezable> オブジェクトをフリーズするには、`PresentationOptions:Freeze` 属性を使用します。  次の例では、<xref:System.Windows.Media.SolidColorBrush> を、フリーズされたページ リソースとして宣言します。  次に、このブラシを使用してボタンの背景を設定します。  
  
 [!code-xml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 `Freeze` 属性を使用するには、表示オプション名前空間 `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` に割り当てる必要があります。  この名前空間を割り当てるときの推奨プレフィックスは `PresentationOptions` です。  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 すべての XAML リーダーがこの属性を認識するとは限らないので、[mc:Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)を使用して、`Presentation:Freeze` 属性が無視可能であると指定することをお勧めします。  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 詳細については、[mc:Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)のページを参照してください。  
  
### Freezable の "フリーズ解除"  
 <xref:System.Windows.Freezable> をフリーズすると、変更やフリーズ解除はできなくなりますが、<xref:System.Windows.Freezable.Clone%2A> メソッドまたは <xref:System.Windows.Freezable.CloneCurrentValue%2A> メソッドを使用すると、フリーズされていない複製を作成できます。  
  
 次の例では、ブラシを使用してボタンの背景を設定してから、そのブラシをフリーズします。  <xref:System.Windows.Freezable.Clone%2A> メソッドを使用して、ブラシのフリーズされていない複製を作成します。  この複製を変更し、使用して、ボタンの背景を黄色から赤に変更します。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  使用する Clone メソッドにかかわらず、アニメーションが新しい <xref:System.Windows.Freezable> にコピーされることはありません。  
  
 <xref:System.Windows.Freezable.Clone%2A> メソッドと <xref:System.Windows.Freezable.CloneCurrentValue%2A> メソッドは、フリーズ可能オブジェクトの深いコピーを生成します。  フリーズ可能オブジェクトに、他のフリーズされたフリーズ可能オブジェクトが格納されている場合は、格納されるオブジェクトも複製されて、変更可能になります。  たとえば、フリーズされた <xref:System.Windows.Media.PathGeometry> を複製して変更可能にする場合は、格納されている数字およびセグメントもコピーされ、変更可能な状態になります。  
  
<a name="createyourownfreezableclass"></a>   
## 独自の Freezable クラスの作成  
 <xref:System.Windows.Freezable> から派生するクラスには、次の機能が与えられます。  
  
-   特殊な状態 : 読み取り専用 \(フリーズ\) 状態と書き込み可能状態。  
  
-   スレッド セーフ : フリーズされた <xref:System.Windows.Freezable> は、スレッド間で共有できます。  
  
-   詳細な変更通知 : 他の <xref:System.Windows.DependencyObject> とは異なり、Freezable オブジェクトは、サブプロパティの値が変更されたときに変更通知を提供します。  
  
-   容易な複製 : Freezable クラスは、深い複製を作成するためのメソッドを既に実装しています。  
  
 <xref:System.Windows.Freezable> は、<xref:System.Windows.DependencyObject> の一種であるので、依存関係プロパティ システムを使用します。  作成するクラスのプロパティが依存関係プロパティである必要はありませんが、<xref:System.Windows.Freezable> クラスは依存関係プロパティを想定して設計されているので、依存関係プロパティを使用すれば、プログラミングに必要なコードの量が少なくて済みます。  依存関係プロパティ システムの詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
 <xref:System.Windows.Freezable> のすべてのサブクラスで <xref:System.Windows.Freezable.CreateInstanceCore%2A> メソッドをオーバーライドする必要があります。  作成するクラスで、すべてのデータについて依存関係プロパティを使用する場合は、これで完了です。  
  
 クラスに依存関係プロパティ以外のデータ メンバーが含まれている場合は、次のメソッドもオーバーライドする必要があります。  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 また、依存関係プロパティではないデータ メンバーへのアクセスおよび書き込みについては、次のルールに従う必要があります。  
  
-   依存関係プロパティ以外のデータ メンバーを読み取る [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] の開始時に、<xref:System.Windows.Freezable.ReadPreamble%2A> メソッドを呼び出します。  
  
-   依存関係プロパティ以外のデータ メンバーを書き込む API の開始時に、<xref:System.Windows.Freezable.WritePreamble%2A> メソッドを呼び出します   \([!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] の中で <xref:System.Windows.Freezable.WritePreamble%2A> を呼び出した後は、依存関係プロパティ以外のデータ メンバーを読み取る場合も、<xref:System.Windows.Freezable.ReadPreamble%2A> を改めて呼び出す必要はありません\)。  
  
-   依存関係プロパティ以外のデータ メンバーに書き込みを行うメソッドを終了する前に、<xref:System.Windows.Freezable.WritePostscript%2A> メソッドを呼び出します。  
  
 作成するクラスに含まれる、依存関係プロパティ以外のデータ メンバーの中に <xref:System.Windows.DependencyObject> オブジェクトがある場合は、そのメンバーの値を変更するたびに <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> メソッドも呼び出す必要があります \(そのメンバーを `null` に設定する場合も\)。  
  
> [!NOTE]
>  オーバーライドする <xref:System.Windows.Freezable> の各メソッドの先頭で基本実装を呼び出すことが非常に重要です。  
  
 カスタム <xref:System.Windows.Freezable> クラスの例については、[カスタム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=159981)を参照してください。  
  
## 参照  
 <xref:System.Windows.Freezable>   
 [カスタム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=159981)   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)