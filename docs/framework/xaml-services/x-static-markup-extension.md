---
title: "x:Static Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticExtension"
  - "xStatic"
  - "x:Static"
helpviewer_keywords: 
  - "x:Static markup extension [XAML Services]"
  - "Static markup extension in XAML [XAML Services]"
  - "XAML [XAML Services], x:Static markup extension"
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: 25
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 25
---
# x:Static Markup Extension
[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] に準拠した方法で定義された静的な値渡しコード エンティティを参照します。  参照先の静的プロパティを使用して、XAML でプロパティの値を指定できます。  
  
## XAML 属性の使用方法  
  
```  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`prefix`|省略可能です。  割り当てられた、既定以外の XAML 名前空間を参照するプレフィックス。  既定の XAML 名前空間から派生した静的プロパティを参照する機会はほとんどないので、実際の用途では `prefix` が明示的に使用されます。  「解説」を参照してください。|  
|`typeName`|必ず指定します。  目的の静的なメンバーを定義する型の名前です。|  
|`staticMemberName`|必ず指定します。  目的の静的な値メンバーの名前 \(定数、静的プロパティ、フィールド、または列挙値\)。|  
  
## 解説  
 参照されるコード エンティティは次のいずれかにする必要があります。  
  
-   定数  
  
-   静的プロパティ  
  
-   フィールド  
  
-   列挙値  
  
 非静的プロパティなど、他のコード エンティティを指定すると、XAML のマークアップ コンパイル時にエラーが発生したり、XAML の読み込み時に解析例外が発生したりします。  
  
 現在の XAML ドキュメントの既定の XAML 名前空間内にない静的なフィールドやプロパティに対して `x:Static` 参照を作成することはできますが、これにはプレフィックスの割り当てが必要です。  ほとんどの場合、XAML 名前空間は、XAML ドキュメントのルート要素で定義されます。  
  
 静的プロパティのルックアップ操作は、既定の XAML スキーマ コンテキストで実行する場合、.NET Framework XAML サービスおよびその XAML リーダーと XAML ライターで実行できます。  この XAML スキーマ コンテキストでは、CLR リフレクションを使用して、オブジェクト グラフの構築に必要な静的な値を指定できます。  指定する `typeName` は、実際には XAML の型名であって、CLR の型名ではありません。ただし、既定の XAML スキーマ コンテキストを使用する場合、またはすべて CLR ベースの既存の XAML 実装フレームワークを使用する場合、両者は基本的には同じ名前となります。  
  
 直接にはプロパティの値の型ではない `x:Static` 参照を作成する際には注意が必要です。  XAML の処理シーケンスでは、マークアップ拡張機能で指定した値に対して、さらに値変換が行われることはありません。  これは、`x:Static` 参照によって作成されるのがテキスト文字列でも同じであり、テキスト文字列に基づく属性値の値変換は、通常、特定のメンバーまたは戻り値の型の任意のメンバーに対して行われます。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。  `x:Static` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.StaticExtension> 拡張クラスの <xref:System.Windows.Markup.StaticExtension.Member%2A> 値として割り当てられます。  
  
 これ以外にも、技術的には可能な XAML の使用方法としては、次の 2 種類が挙げられます。  ただし、次の使用方法は必要以上に冗長なので、あまり一般的ではありません。  
  
 **オブジェクト要素構文:** `<x:Static Member="``prefix``:``typeName``.``staticMemberName``" .../>`  
  
 **初期化文字列の明示的なメンバー プロパティを含む属性構文:** `<``object````property``="{x:Static Member=``prefix``:``typeName``.``staticMemberName``}" .../>`  
  
 .NET Framework XAML サービス実装では、このマークアップ拡張機能の処理は、<xref:System.Windows.Markup.StaticExtension> クラスによって定義されます。  
  
 `x:Static` はマークアップ拡張機能です。  XAML のすべてのマークアップ拡張機能では、それぞれの属性構文で `{` と `}` の 2 つの記号を使用します。これは規約であり、これに従って XAML プロセッサは、マークアップ拡張機能で値を指定する必要があることを認識します。  マークアップ拡張機能の詳細については、「[Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)」を参照してください。  
  
## WPF の使用上の注意  
 WPF プログラミングで使用する既定の XAML 名前空間には、有用な静的プロパティはそれほど数多くは用意されていません。また、有用な静的プロパティのほとんどで、型コンバーターなどの機能がサポートされており、特に `{x:Static}` を使用する必要はありません。  次のいずれかに該当する場合、静的プロパティに対して、XAML 名前空間のプレフィックスを割り当てる必要があります。  
  
-   WPF 内に存在するが、WPF の既定の XAML 名前空間 \([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]\) の一部ではない型を参照している場合。  これは、`x:Static` を使用する非常に一般的なシナリオです。  たとえば、<xref:System.Environment> クラスの静的プロパティを参照するためには、<xref:System> CLR 名前空間と mscorlib アセンブリに割り当てられた XAML 名前空間を持つ `x:Static` 参照を使用できます。  
  
-   カスタム アセンブリの型を参照している場合。  
  
-   WPF アセンブリ内に存在する型を参照しているが、その型が WPF の既定の XAML 名前空間の一部になるように割り当てられた名前空間以外の CLR 名前空間内にある場合。  WPF の既定の XAML 名前空間への CLR 名前空間の割り当ては、各種 WPF アセンブリ \(この概念の詳細については、「[XAML 名前空間および WPF XAML の名前空間の割り当て](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照\) の定義に基づいて実行されます。  未割り当ての CLR 名前空間は、その CLR 名前空間の大部分が、<xref:System.Windows.Threading> など、通常、XAML では使用されないクラス定義で構成される場合に存在できます。  
  
 WPF でのプレフィックスおよび XAML 名前空間の使用方法の詳細については、「[XAML 名前空間および WPF XAML の名前空間の割り当て](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
## 参照  
 [x:Type Markup Extension](../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)