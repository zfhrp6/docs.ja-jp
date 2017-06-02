---
title: "XAML 読み込みと依存関係プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "カスタム依存関係プロパティ"
  - "依存関係プロパティ, XAML 読み込みおよび"
  - "読み込み (XML データを) "
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# XAML 読み込みと依存関係プロパティ
現在の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 実装の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、依存関係プロパティに最初から対応しています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、バイナリ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を読み込むとき、および依存関係プロパティである属性を処理するときに、依存関係プロパティ用のプロパティ システム メソッドを使用します。  この結果、プロパティ ラッパーは実質的に省略されます。  カスタムの依存関係プロパティを実装するときには、この動作を考慮に入れて、プロパティ システム メソッド <xref:System.Windows.DependencyObject.GetValue%2A> および <xref:System.Windows.DependencyObject.SetValue%2A> 以外のコードをプロパティ ラッパーに記述することは避ける必要があります。  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックは、依存関係プロパティを使用と作成の両面から理解していることと、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」および「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を通読していることを前提としています。  また、「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」および「[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」も通読している必要があります。  
  
<a name="implementation"></a>   
## WPF XAML ローダーの実装とパフォーマンス  
 実装上の理由から、プロパティを依存関係プロパティとして指定して、プロパティ システムの <xref:System.Windows.DependencyObject.SetValue%2A> メソッドを使用して設定する方が、プロパティ ラッパーおよびその setter を使用するよりも、処理の負荷が抑えられます。  その理由は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、マークアップとさまざまな文字列の構造で示された、型とメンバーの関係を把握し、それだけを頼りに、基になるコードのオブジェクト モデル全体を推論する必要があるためです。  
  
 型は xmlns とアセンブリ属性の組み合わせで検索されますが、メンバーの識別、属性として設定された値をどれがサポートするかの判断、およびプロパティ値がどの型をサポートするかの解決は、<xref:System.Reflection.PropertyInfo> によるリフレクションを多用することになります。  任意の型の依存関係プロパティは、プロパティ システムを通じてストレージ テーブルとしてアクセスできます。このため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 実装の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、このテーブルを使用します。そして、プロパティ *ABC* を設定するには、依存関係プロパティ識別子 *ABCProperty* を使用して、所属する <xref:System.Windows.DependencyObject.SetValue%2A> 派生型の <xref:System.Windows.DependencyObject> を呼び出す方が効率がよいと推論します。  
  
<a name="implications"></a>   
## カスタム依存関係プロパティでの影響  
 現在の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 実装の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサでは、プロパティ設定の動作でラッパーが完全に省略されるため、カスタム依存関係プロパティのラッパーの set の定義には、追加的なロジックを記述しないことが必要です。  追加的なロジックを set の定義に記述した場合、プロパティがコードではなく [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で設定されたときには、ロジックは実行されません。  
  
 同様に、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサが [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 処理からプロパティ値を取得するときにも、ラッパーではなく <xref:System.Windows.DependencyObject.GetValue%2A> が使用されます。  したがって、`get` の定義では、<xref:System.Windows.DependencyObject.GetValue%2A> の呼び出し以外に追加的な処理を実装することは避ける必要があります。  
  
 次の例は、依存関係プロパティで推奨される定義方法です。ラッパーを使用して、プロパティ識別子は `public` `static` `readonly` フィールドとして格納し、`get` と `set` の定義には、依存関係プロパティのバッキングを定義するために必要なプロパティ システム メソッド以外のコードは含まれていません。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## 参照  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [コレクション型依存関係プロパティ](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)   
 [依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)   
 [DependencyObject の安全なコンストラクター パターン](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)