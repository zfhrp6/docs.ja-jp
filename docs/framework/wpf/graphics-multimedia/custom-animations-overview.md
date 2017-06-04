---
title: "カスタム アニメーションの概要 | Microsoft Docs"
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
  - "アニメーション, カスタム クラス"
  - "カスタム アニメーション クラス"
  - "カスタム クラス, アニメーション"
  - "カスタム キー フレーム"
  - "キー フレーム, カスタム"
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# カスタム アニメーションの概要
ここでは、カスタム キー フレームまたはアニメーション クラスを作成するか、フレームごとのコールバックを使用してアニメーション システムをバイパスすることにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション システムを拡張する方法とタイミングを説明します。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要条件  
 このトピックを理解するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が提供するさまざまな種類のアニメーションに精通している必要があります。  詳細については、「[From\/To\/By アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md)」、「[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)」、および「[パス アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)」を参照してください。  
  
 アニメーション クラスは <xref:System.Windows.Freezable> クラスを継承するため、<xref:System.Windows.Freezable> オブジェクトおよび <xref:System.Windows.Freezable> クラスの継承方法に精通している必要があります。  詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
<a name="extendingtheanimationsystem"></a>   
## アニメーション システムの拡張  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション システムの拡張方法は、使用する組み込み機能のレベルに応じて多数あります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション エンジンには、次の 3 つの主要な拡張ポイントがあります。  
  
-   <xref:System.Windows.Media.Animation.DoubleKeyFrame> など *\<Type\>*KeyFrame クラスの 1 つを継承することにより、カスタム キー フレーム オブジェクトを作成します。  この方法では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション エンジンの組み込み機能のほとんどを使用します。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline> を継承するか、*\<Type\>*AnimationBase クラスの 1 つを継承することにより、独自のアニメーション クラスを作成します。  
  
-   フレームごとのコールバックを使用してフレーム ベースのアニメーションを生成します。  この方法は、アニメーションとタイミング システムを完全にバイパスします。  
  
 アニメーション システムを拡張するためのいくかのシナリオを次の表に示します。  
  
|目的|使用する方法|  
|--------|------------|  
|対応する *\<Type\>*AnimationUsingKeyFrames を持つ型の値間の補間をカスタマイズする|カスタム キー フレームを作成します。  詳細については、「[カスタム キー フレームの作成](#createacustomkeyframe)」を参照してください。|  
|対応する *\<Type\>*Animation を持つ型の値間の補間以上のものもカスタマイズする|アニメーション化する型に対応する *\<Type\>*AnimationBase クラスを継承する、カスタム アニメーション クラスを作成します。  詳細については、「[カスタム アニメーション クラスの作成](#createcustomanimationtype)」を参照してください。|  
|対応する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーションを持たない型をアニメーション化する|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> を使用するか、<xref:System.Windows.Media.Animation.AnimationTimeline> を継承するクラスを作成します。  詳細については、「[カスタム アニメーション クラスの作成](#createcustomanimationtype)」を参照してください。|  
|オブジェクトの最後の一連のやり取りに基づいてフレームごとに計算された値で、複数のオブジェクトをアニメーション化する|フレームごとのコールバックを使用します。  詳細については、「[フレームごとのコールバックの使用](#useperframecallback)」を参照してください。|  
  
<a name="createacustomkeyframe"></a>   
## カスタム キー フレームの作成  
 カスタム キー フレーム クラスの作成は、アニメーション システムを拡張する最も簡単な方法です。  この方法は、キーフレーム アニメーションに対して別の補間方式が必要な場合に使用します。  「[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)」で説明しているように、キー フレーム アニメーションは、キー フレーム オブジェクトを使用してその出力値を生成します。  各キー フレームオブジェクトは、次の 3 つの機能を実行します。  
  
-   その <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> プロパティを使用してターゲットの値を指定します。  
  
-   その <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> プロパティを使用して値に達する時間を指定します。  
  
-   InterpolateValueCore メソッドを実装して、前のキー フレームの値とその独自の値の間を補間します。  
  
 **実装手順**  
  
 *\<Type\>*KeyFrame 抽象クラスから派生して、InterpolateValueCore メソッドを実装します。  InterpolateValueCore メソッドは、キー フレームの現在の値を返します。  このメソッドは、前のキー フレームの値と、0 ～ 1 の進行状況を示す値の 2 つのパラメーターを受け取ります。  進行状況 0 は、キー フレームが開始したばかりであることを示し、1 は、キー フレームが完了したばかりで、その <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> プロパティで指定された値を返す必要があることを示します。  
  
 *\<Type\>*KeyFrame クラスは <xref:System.Windows.Freezable> クラスを継承するため、<xref:System.Windows.Freezable.CreateInstanceCore%2A> コアをオーバーライドして、クラスの新しいインスタンスを返す必要もあります。  クラスがデータの格納に[依存関係プロパティ](GTMT)を使用していない場合や、作成後に追加の初期化を必要とする場合は、状況に応じて上記以外のメソッドをオーバーライドする必要が生じます。詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 カスタムの *\<Type\>*KeyFrame アニメーションを作成した後に、その型の *\<Type\>*AnimationUsingKeyFrames でこのアニメーションを使用できます。  
  
<a name="createacustomanimationtype"></a>   
## カスタム アニメーション クラスの作成  
 独自の種類のアニメーションを作成すると、オブジェクトをアニメーション化する方法を制御しやすくなります。  独自の種類のアニメーションを作成するための 2 つの推奨方法として、<xref:System.Windows.Media.Animation.AnimationTimeline> クラスから派生する方法と、*\<Type\>*AnimationBase クラスから派生する方法があります。  *\<Type\>*Animation クラスまたは *\<Type\>*AnimationUsingKeyFrames クラスからの派生はお勧めしません。  
  
### \<Type\>AnimationBase からの派生  
 *\<Type\>*AnimationBase クラスから派生する方法は、新しいアニメーションの種類を作成する最も簡単な方法です。  対応する *\<Type\>*AnimationBase クラスが既にある種類の新しいアニメーションを作成する場合は、この方法を使用します。  
  
 **実装手順**  
  
 *\<Type\>*Animation クラスから派生して、GetCurrentValueCore メソッドを実装します。  GetCurrentValueCore メソッドは、アニメーションの現在の値を返します。  このメソッドは、提示される開始値および終了値、およびアニメーションの進行状況を確認するために使用する <xref:System.Windows.Media.Animation.AnimationClock> の 3 つのパラメーターをとります。  
  
 *\<Type\>*AnimationBase クラスは <xref:System.Windows.Freezable> クラスを継承するため、<xref:System.Windows.Freezable.CreateInstanceCore%2A> コアをオーバーライドして、クラスの新しいインスタンスを返す必要もあります。  クラスがデータの格納に[依存関係プロパティ](GTMT)を使用していない場合や、作成後に追加の初期化を必要とする場合は、状況に応じて上記以外のメソッドをオーバーライドする必要が生じます。詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 詳細については、アニメーション化する型の *\<Type\>*AnimationBase クラスの GetCurrentValueCore メソッドのドキュメントを参照してください。  例については、[カスタム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=159981)を参照してください。  
  
 **別の方法**  
  
 単にアニメーション値を補間する方法を変更する場合は、*\<Type\>*KeyFrame クラスの 1 つから派生することをお勧めします。  作成したキー フレームは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が提供する、対応する *\<Type\>*AnimationUsingKeyFrames で使用できます。  
  
### AnimationTimeline からの派生  
 一致する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーションを持っていない型に対してアニメーションを作成する場合や、厳密に型指定されていないアニメーションを作成する場合は、<xref:System.Windows.Media.Animation.AnimationTimeline> クラスから派生します。  
  
 **実装手順**  
  
 <xref:System.Windows.Media.Animation.AnimationTimeline> クラスから派生して、次のメンバーをオーバーライドします。  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A> – 新しいクラスが具象クラスである場合、<xref:System.Windows.Freezable.CreateInstanceCore%2A> をオーバーライドしてクラスの新しいインスタンスを返す必要があります。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – このメソッドをオーバーライドして、アニメーションの現在の値を返します。  このメソッドは、既定の開始値、既定の終了値、および <xref:System.Windows.Media.Animation.AnimationClock> の 3 つのパラメーターをとります。  <xref:System.Windows.Media.Animation.AnimationClock> を使用して、現在の時刻またはアニメーションの進行状況を取得します。  既定の開始値および終了値を使用するかどうかを選択できます。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – このプロパティをオーバーライドして、<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> メソッドで指定されている既定の終了値をアニメーションで使用するかどうかを示します。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – このプロパティをオーバーライドして、アニメーションが生成する出力値の <xref:System.Type> を示します。  
  
 クラスがデータの格納に[依存関係プロパティ](GTMT)を使用していない場合や、作成後に追加の初期化を必要とする場合は、状況に応じて上記以外のメソッドをオーバーライドする必要が生じます。詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 \([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーションで使用される\) 推奨されるパラダイムは、次の 2 つの継承レベルを使用することです。  
  
1.  <xref:System.Windows.Media.Animation.AnimationTimeline> から派生した抽象 *\<Type\>*AnimationBase クラスを作成します。  このクラスは、<xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> メソッドをオーバーライドする必要があります。  また、新しい抽象メソッド GetCurrentValueCore を導入し、<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> をオーバーライドして、既定の開始値パラメーターと既定の終了値パラメーターの型を検証してから、GetCurrentValueCore を呼び出す必要があります。  
  
2.  新しい *\<Type\>*AnimationBase クラスを継承する別のクラスを作成し、<xref:System.Windows.Freezable.CreateInstanceCore%2A> メソッド、導入した GetCurrentValueCore メソッド、および <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> プロパティをオーバーライドします。  
  
 **別の方法**  
  
 対応する From\/To\/By アニメーションまたはキーフレーム アニメーションを持たない型をアニメーション化する場合は、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> の使用をお勧めします。  <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> は弱く型指定されているため、どの型の値でもアニメーション化できます。  この方法の欠点は、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> が[離散補間](GTMT)のみをサポートするということです。  
  
<a name="useperframecallback"></a>   
## フレームごとのコールバックの使用  
 この方法は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション システムを完全にバイパスする必要がある場合に使用します。  この方法の 1 つのシナリオは、アニメーションの各ステップで、オブジェクトの最後の一連のやり取りに基づいてアニメーション化されたオブジェクトの新しい方向や位置の再計算が必要になる物理アニメーションです。  
  
 **実装手順**  
  
 これまで説明してきた他の方法とは異なり、フレームごとのコールバックを使用する場合、カスタムのアニメーションやキー フレームのクラスを作成する必要はありません。  
  
 代わりに、アニメーション化するオブジェクトを格納しているオブジェクトの <xref:System.Windows.Media.CompositionTarget.Rendering> イベントで登録します。  このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が[ビジュアル ツリー](GTMT)の永続化されたレンダリング データを構成ツリーにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。  
  
 イベント ハンドラーでは、アニメーション効果に必要なあらゆる計算を実行し、これらの値を使用してアニメーション化するオブジェクトのプロパティを設定します。  
  
 現在のフレームの表現時間を取得するには、このイベントに関連付けられている <xref:System.EventArgs> を、<xref:System.Windows.Media.RenderingEventArgs> としてキャストできます。これにより、現在のフレームのレンダリング時間を取得するために使用できる <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> プロパティが提供されます。  
  
 詳細については、<xref:System.Windows.Media.CompositionTarget.Rendering> のページを参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.AnimationTimeline>   
 <xref:System.Windows.Media.Animation.IKeyFrame>   
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [From\/To\/By アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md)   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [パス アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [カスタム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=159981)