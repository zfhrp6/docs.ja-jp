---
title: "コレクション型依存関係プロパティ | Microsoft Docs"
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
  - "コレクション型プロパティ"
  - "依存関係プロパティ"
  - "プロパティ, コレクション型"
  - "プロパティ, 依存関係"
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# コレクション型依存関係プロパティ
ここでは、プロパティの型がコレクション型である場合に[依存関係プロパティ](GTMT)を実装する方法についての、ガイダンスと推奨されるパターンを示します。  
  
   
  
<a name="implementing"></a>   
## コレクション型依存関係プロパティの実装  
 一般に、依存関係プロパティの場合、使用する実装パターンは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティ ラッパーを定義するものです。この場合、そのプロパティは、フィールドや他の構造ではなく <xref:System.Windows.DependencyProperty> 識別子によってサポートされます。  コレクション型プロパティを実装するときは、これと同じパターンに従います。  ただし、コレクションに含まれる型それ自体が <xref:System.Windows.DependencyObject> または <xref:System.Windows.Freezable> の派生クラスである場合は常に、コレクション型プロパティを使用することでパターンは複雑になります。  
  
<a name="initializing"></a>   
## 既定値を上回るコレクションの初期化  
 依存関係プロパティを作成するときは、初期フィールド値としてプロパティの既定値を指定しません。  代わりに、依存関係プロパティのメタデータを使用して既定値を指定します。  プロパティが参照型の場合、依存関係プロパティのメタデータで指定する既定値はインスタンスごとの既定値ではありません。その型のすべてのインスタンスに適用される既定値です。  したがって、コレクション プロパティ メタデータによって定義される単一の静的コレクションを、その型の新しく作成されるインスタンスの作業既定値として使用しないように注意してください。  代わりに、クラス コンストラクターのロジックの一部として、コレクションの値に一意 \(インスタンス\) のコレクションを意図的に設定する必要があります。  それ以外の場合は、意図しないシングルトン クラスを作成することになります。  
  
 例を次に示します。  この例は、`Aquarium` クラスの定義を示しています。  このクラスで定義されているコレクション型依存関係プロパティ `AquariumObjects` は、<xref:System.Windows.FrameworkElement> 型の制約でジェネリック <xref:System.Collections.Generic.List%601> 型を使用します。  依存関係プロパティに対する <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> の呼び出しでは、メタデータが、既定値を新しいジェネリック <xref:System.Collections.Generic.List%601> に設定します。  
  
 <!-- TODO: review snippet reference [!code-csharp[PropertiesOvwSupport#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemdefinition)]  -->
 [!code-vb[PropertiesOvwSupport#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemdefinition)]  
[!code-csharp[PropertiesOvwSupport#CollectionProblemEndB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemendb)]
[!code-vb[PropertiesOvwSupport#CollectionProblemEndB](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemendb)]  
  
 ただし、コードをこのままにすると、単一のリストの既定値が `Aquarium` のすべてのインスタンスで共有されます。  次のテスト コードは、2 つの異なる `Aquarium` インスタンスをインスタンス化し、それぞれに単一の異なる `Fish` を追加する方法を示していますが、これを実行すると、想定外の結果になります。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 各コレクションのカウントが 1 になるのではなく、いずれのコレクションもカウントが 2 になります。  これは、各 `Aquarium` は `Fish` を既定値のコレクションに追加しますが、その基になっているのはメタデータでの単一のコンストラクター呼び出しであり、したがってすべてのインスタンス間で共有されるためです。  これは望ましい状況ではありません。  
  
 この問題を回避するには、クラス コンストラクターの呼び出しの一部として、コレクションの依存関係プロパティの値を一意のインスタンスにリセットする必要があります。  プロパティは読み取り専用の依存関係プロパティであるため、クラス内だけでアクセスできる <xref:System.Windows.DependencyPropertyKey> を使用し、<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> メソッドを使用して設定します。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 再びテスト コードを実行すると、結果は期待したものに近くなり、各 `Aquarium` が独自の一意のコレクションをサポートします。  
  
 コレクション プロパティを読み取り\/書き込みにすると、このパターンには若干のバリエーションが発生します。  この場合は、コンストラクターからパブリック set アクセサーを呼び出して初期化を行うことができ、パブリック <xref:System.Windows.DependencyProperty> 識別子を使用して、set ラッパー内でキーなしのシグネチャの <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> を呼び出します。  
  
## コレクション プロパティからのバインディング値変更の報告  
 それ自体が依存関係プロパティであるコレクション プロパティは、変更をサブプロパティに自動的には報告しません。  コレクションにバインディングを作成している場合は、これによってバインディングが変更を報告しないことがあり、一部のデータ バインディング シナリオが無効になります。  ただし、コレクション型として <xref:System.Windows.FreezableCollection%601> を使用している場合は、コレクションに含まれる要素に対するサブプロパティの変更は正しく報告され、バインディングは意図したとおりに動作します。  
  
 依存関係オブジェクト コレクションでサブプロパティのバインディングを有効にするには、<xref:System.Windows.FreezableCollection%601> 型としてコレクション プロパティを作成し、そのコレクションの型制約を <xref:System.Windows.DependencyObject> 派生クラスに指定します。  
  
## 参照  
 <xref:System.Windows.FreezableCollection%601>   
 [WPF における XAML とカスタム クラス](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)