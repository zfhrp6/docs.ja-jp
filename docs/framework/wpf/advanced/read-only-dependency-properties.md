---
title: "読み取り専用の依存関係プロパティ | Microsoft Docs"
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
  - "依存関係プロパティ, 読み取り専用"
  - "読み取り専用の依存関係プロパティ"
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 読み取り専用の依存関係プロパティ
ここでは、既存の読み取り専用依存関係プロパティ、カスタムの読み取り専用依存関係プロパティを作成するシナリオと手法など、読み取り専用依存関係プロパティについて説明します。  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックでは、依存プロパティの実装の基本シナリオとカスタム依存プロパティへのメタデータの適用方法を理解していることを前提とします。  詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」および「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  
  
<a name="existing"></a>   
## 既存の読み取り専用依存関係プロパティ  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] フレームワークで定義されている依存関係プロパティの一部は読み取り専用です。  読み取り専用依存関係プロパティを指定する一般的な理由は、状態決定に使用する必要のあるプロパティがあるけれども、その状態は多くの要因から影響を受け、プロパティをその状態に設定するだけでは、ユーザー インターフェイス設計の観点から望ましくないためです。  たとえば、<xref:System.Windows.UIElement.IsMouseOver%2A> プロパティは、実際にはマウス入力から決定される単なるサーフェイス状態です。  実際にマウス入力を行わずにプログラムでこの値を設定しようとすると、結果は予想できず、不整合が発生する可能性があります。  
  
 設定可能ではないため、読み取り専用の依存関係プロパティは、依存関係プロパティがソリューションを通常提供するシナリオの多くには適切ではありません \(データ バインディング、直接スタイル設定可能な値、検証、アニメーション、継承など\)。  それでも、設定不可能な読み取り専用依存関係プロパティには、プロパティ システムの依存関係プロパティによってサポートされるいくつかの追加機能があります。  最も重要な機能は、読み取り専用依存関係プロパティはスタイルのプロパティ トリガーとして使用できることです。  通常の [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティではトリガーを有効にできません。依存関係プロパティであることが必要です。  上で挙げた <xref:System.Windows.UIElement.IsMouseOver%2A> プロパティは、コントロールのスタイルを定義するために便利なシナリオのよい例です。背景、前景、またはコントロール内の複合要素の同種のプロパティなどの一部の表示プロパティは、コントロールの定義済み領域にユーザーがマウスを置くと変化します。  読み取り専用依存関係プロパティの変化は、プロパティ システム固有の検証プロセスによって検出して報告することもでき、これは実際にはプロパティ トリガー機能を内部的にサポートします。  
  
<a name="new"></a>   
## 読み取り専用のカスタム依存プロパティの作成  
 多くの一般的な依存関係プロパティのシナリオで読み取り専用依存関係プロパティが機能しない理由に関する前のセクションを参照してください。  ただし、適切なシナリオがある場合は、独自の読み取り専用依存関係プロパティを作成してもかまいません。  
  
 読み取り専用依存関係プロパティを作成するプロセスのほとんどは、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」および「[依存関係プロパティを実装する](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md)」の説明と同じです。  ただし、次の 3 つの重要な違いがあります。  
  
-   プロパティを登録するときは、プロパティ登録用の通常の <xref:System.Windows.DependencyProperty.Register%2A> メソッドではなく、<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> メソッドを呼び出します。  
  
-   [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] の "ラッパー" プロパティを実装するときは、ラッパーにも set 実装をしないようにして、公開するパブリック ラッパーの読み取り専用状態が矛盾しないようにする必要があります。  
  
-   読み取り専用の登録によって返されるオブジェクトは、<xref:System.Windows.DependencyProperty> ではなく <xref:System.Windows.DependencyPropertyKey> です。  やはりこのフィールドをメンバーとして格納する必要がありますが、通常は、型のパブリック メンバーにはしません。  
  
 読み取り専用依存関係プロパティを補足するために使用するプライベートのフィールドまたは値はすべて、適当なロジックを使用して完全に書き込み可能にしてかまいません。  ただし、初期化で、またはランタイム ロジックの一部として、プロパティを設定する最も簡単な方法は、プロパティ システムを使用しないでプライベートな補足フィールドを直接設定するのではなく、プロパティ システムの [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を使用する方法です。  具体的には、<xref:System.Windows.DependencyPropertyKey> 型のパラメーターを受け取る <xref:System.Windows.DependencyObject.SetValue%2A> のシグネチャがあります。  アプリケーション ロジック内でプログラムによってこの値を設定する方法と場所により、依存関係プロパティを最初に登録したときに作成される <xref:System.Windows.DependencyPropertyKey> に対するアクセスの設定方法が影響を受けます。  このロジックすべてをクラス内で処理する場合はプライベートにでき、アセンブリの他の部分から設定する必要がある場合は内部に設定します。  1 つの方法は、格納されているプロパティ値の変更が必要であることをクラスのインスタンスに通知する関連イベントのクラス イベント ハンドラー内で、<xref:System.Windows.DependencyObject.SetValue%2A> を呼び出すというものです。  もう 1 つの方法は、登録の際にプロパティのメタデータの一部として、ペアになった <xref:System.Windows.PropertyChangedCallback> コールバックと <xref:System.Windows.CoerceValueCallback> コールバックを使用して、依存関係プロパティを結び付けるというものです。  
  
 <xref:System.Windows.DependencyPropertyKey> はプライベートであり、コードの外部のプロパティ システムによっては伝達されないので、読み取り専用依存関係プロパティの方が、読み取り\/書き込み依存関係プロパティより設定のセキュリティが優れています。  読み取り\/書き込み依存関係プロパティの場合は、識別するフィールドは明示的または暗黙的にパブリックであり、したがってプロパティは広範に設定可能です。  詳細については、「[依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)」を参照してください。  
  
## 参照  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)