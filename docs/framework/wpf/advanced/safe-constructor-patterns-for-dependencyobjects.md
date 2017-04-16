---
title: "DependencyObject の安全なコンストラクター パターン | Microsoft Docs"
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
  - "依存関係オブジェクトのコンストラクター パターン"
  - "依存関係オブジェクト, コンストラクター パターン"
  - "FXCop ツール"
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# DependencyObject の安全なコンストラクター パターン
通常、クラスのコンストラクターでは、仮想メソッドやデリゲートなどのコールバックは呼び出しません。コンストラクターは派生クラスのコンストラクターの基底の初期化として呼び出されることがあるためです。  対象のオブジェクトの初期化が不完全な状態で仮想メソッドに入る可能性があります。  ただし、プロパティ システム自体は依存関係プロパティ システムの一部としてコールバックを呼び出し、内部的に公開します。  <xref:System.Windows.DependencyObject.SetValue%2A> の呼び出しによって依存関係プロパティの値を設定するような簡単な演算には、決定のどこかにコールバックが潜在的に含まれます。  この理由から、使用する型が基本クラスとして使われる場合に、コンストラクターの本文で依存関係プロパティの値を設定すると問題が起こる可能性があるため、注意する必要があります。  <xref:System.Windows.DependencyObject> コンストラクターを実装するときには、依存関係プロパティの状態および付随するコールバックに関する固有の問題を回避するための特定のパターンがあります。ここでは、そのパターンについて説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Property_System_Virtual_Methods"></a>   
## プロパティ システムの仮想メソッド  
 依存関係プロパティの値を設定する <xref:System.Windows.DependencyObject.SetValue%2A> の呼び出しの計算中には、<xref:System.Windows.ValidateValueCallback>、<xref:System.Windows.PropertyChangedCallback>、<xref:System.Windows.CoerceValueCallback>、<xref:System.Windows.DependencyObject.OnPropertyChanged%2A> の各仮想メソッドまたはコールバックが潜在的に呼び出されます。  これらの仮想メソッドまたはコールバックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のプロパティ システムと依存関係プロパティの汎用性を高めるうえで、それぞれ特定の目的を果たします。  これらの仮想メソッドを使用してプロパティ値の決定をカスタマイズする方法については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  
  
### FXCop のルール強制とプロパティ システムの仮想メソッドの比較  
 ビルド プロセスの一部として Microsoft ツールの FXCop を使用している場合、基本コンストラクターを呼び出す特定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] フレームワーク クラスを派生させるとき、または派生クラスで独自の依存関係プロパティを実装するときに、FXCop の特定のルール違反が発生することがあります。  この違反に対する名前文字列は、次のとおりです。  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 このルールは、FXCop に設定されている既定のパブリック ルールの一部です。  このルールによって報告されるのは、依存関係プロパティ システムの仮想メソッドを最終的に呼び出す、依存関係プロパティ システム内のトレースです。  このルール違反は、このトピックで説明されている推奨コンストラクター パターンに従っている場合も表示され続けるため、FXCop のルール セット設定でこのルールを無効にするか抑制する必要があります。  
  
### 既存のクラスの使用ではなくクラスの派生が大半の原因  
 このルールによって報告される問題は、コンストラクターで仮想メソッドを呼び出すように実装したクラスが派生される場合に発生します。  クラスをシールする場合、クラスが派生されないとわかっている場合、またはクラスが派生されないように強制する場合は、ここで説明する内容や FXCop のルールによって起こる問題は該当しません。  ただし、テンプレートや拡張可能なコントロール ライブラリのセットを作成する場合などのように、基本クラスとして使用されることを想定したクラスを作成する場合は、ここで説明されているコンストラクターの推奨パターンに従う必要があります。  
  
### 既定のコンストラクターにおいて、コールバックによって要求されるすべての値の初期化の必要性  
 任意のクラスのオーバーライドまたはコールバック \(「プロパティ システムの仮想メソッド」の一覧のコールバック\) によって使用されるすべてのインスタンス メンバーは、クラスの既定のコンストラクターで初期化する必要があります。これは、既定以外のコンストラクターのパラメーターによって値の一部に "実際の" 値が入る場合も同様です。  
  
 次のコード例 \(および以降の例\) は、この規則に違反する擬似 C\# コードの例であり、問題を説明しています。  
  
```  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 アプリケーション コードによって `new MyClass(objectvalue)` が呼び出されると、既定のコンストラクターと基本クラスのコンストラクターが呼び出されます。  次に、`Property1 = object1` が設定されると、対応する `MyClass` <xref:System.Windows.DependencyObject> の仮想メソッドの `OnPropertyChanged` が呼び出されます。  オーバーライドは、まだ初期化されていない `_myList` を参照します。  
  
 これらの問題を回避する方法の 1 つは、コールバックが他の依存関係プロパティだけを使用し、それぞれの使用する依存関係プロパティが、登録済みのメタデータの一部として確立された既定値を持つようにすることです。  
  
<a name="Safe_Constructor_Patterns"></a>   
## 安全なコンストラクター パターン  
 クラスが基本クラスとして使用される場合の不完全な初期化のリスクを回避するには、次のパターンに従います。  
  
#### 基本の初期化を呼び出す既定のコンストラクター  
 次の例では、これらのコンストラクターを実装して、基本の初期化を呼び出します。  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### 既定外の \(簡易\) コンストラクター \(すべての基本シグネチャと一致しない場合\)  
 これらのコンストラクターがパラメーターを使用して初期化の依存関係プロパティを設定する場合は、最初に初期化のための独自のクラスの既定のコンストラクターを呼び出し、次にパラメーターを使用して依存関係プロパティを設定します。  この場合、クラスによって定義された依存関係プロパティ、または基本クラスから継承された依存関係プロパティのどちらかを使用できますが、いずれの場合も次のパターンを使用します。  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### 既定外の \(簡易\) コンストラクター \(基本シグネチャと一致しない場合\)  
 同じパラメーター化を使用して基本コンストラクターを呼び出す代わりに、独自のクラスの既定のコンストラクターを再び呼び出します。  基本初期化子を呼び出さないでください。代わりに、`this()` を呼び出す必要があります。  次に、渡されたパラメーターを関連するプロパティを設定する値として使用し、元のコンストラクターの動作を複製します。  特定のパラメーターを設定するプロパティを決定する場合は、元の基本コンストラクターのドキュメントを参考に使用します。  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### すべてのシグネチャを一致させる必要性  
 基本型が複数のシグネチャを持つ場合は、すべての可能なシグネチャを、さらにプロパティを設定する前に、クラスの既定のコンストラクターを呼び出す推奨パターンを使用する独自のコンストラクターの実装に意図的に一致させる必要があります。  
  
#### SetValue による依存関係プロパティの設定  
 プロパティの設定の利便性のためにラッパーを持たないプロパティを設定し、<xref:System.Windows.DependencyObject.SetValue%2A> を使用して値を設定する場合は、同じパターンが適用されます。  コンストラクター パラメーターを介して渡される <xref:System.Windows.DependencyObject.SetValue%2A> の呼び出しもまた、初期化のためのクラスの既定のコンストラクターを呼び出します。  
  
## 参照  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)