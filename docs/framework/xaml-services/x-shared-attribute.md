---
title: "x:Shared Attribute | Microsoft Docs"
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
  - "XAML [XAML Services], x:Shared attribute"
  - "x:Shared attribute [XAML Services]"
  - "Shared attribute in XAML [XAML Services]"
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: 16
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 16
---
# x:Shared Attribute
`false` に設定されると、WPF リソース取得動作を変更して、すべての要求で同じインスタンスを共有するのではなく、属性付きリソースに対して要求があるたびに新しいインスタンスが作成されるようにします。  
  
## XAML 属性の使用方法  
  
```  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## 解説  
 `x:Shared` は、XAML 言語 XAML 名前空間にマッピングされ、.NET Framework XAML サービスおよびその XAML リーダーによって有効な XAML 言語要素として認識されます。  ただし、`x:Shared` の規定の機能は、WPF アプリケーションおよび WPF XAML パーサーのみに関連しています。  WPF では、`x:Shared` は、WPF <xref:System.Windows.ResourceDictionary> 内に存在するオブジェクトに適用される場合にだけ属性として有用です。  その他の用途では、解析例外や他のエラーはスローされませんが、効果はありません。  
  
 `x:Shared` の意味は、XAML 言語仕様では指定されていません。  .NET Framework XAML サービスに基づいている実装など、その他の XAML 実装は、必ずしもリソース共有をサポートしているとは限りません。  このような XAML 実装は、`x:Shared` 値も使用するフレームワークのサポート時と同様に動作します。  
  
 WPF では、リソースに対する `x:Shared` の既定の状態は `true` です。  この状態は、指定したすべてのリソース要求が常に同じインスタンスを返すことを意味します。  
  
 <xref:System.Windows.FrameworkElement.FindResource%2A> などのリソース API をとおして返されるオブジェクトを変更するか、または <xref:System.Windows.ResourceDictionary> 内で直接オブジェクトを変更すると、元のリソースが変更されます。  そのリソースへの参照が動的リソース参照であった場合、そのリソースのコンシューマーは変更されたリソースを取得するようになります。  
  
 リソースへの参照が静的リソース参照であった場合は、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 処理後にリソースを変更しても無意味です。  静的リソース参照と動的リソース参照の詳細については、「[XAML リソース](../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 `x:Shared="true"` は既定の設定であるため、これを明示的に指定することはあまりありません。  WPF オブジェクト モデルには `x:Shared` と同等の直接的なコードはありません。そのようなコードは、XAML の使用方法でのみ指定でき、既定の WPF 動作によって、または .NET Framework XAML サービスとその XAML リーダーを使用して処理される場合は読み込みパス上の中間 XAML ノード ストリーム内で処理されることが必要です。  
  
 `x:Shared="false"` を指定するシナリオの 1 つに、<xref:System.Windows.FrameworkElement> 派生クラスまたは <xref:System.Windows.FrameworkContentElement> 派生クラスをリソースとして定義し、その要素リソースをコンテンツ モデルに導入する場合があります。  `x:Shared="false"` を指定することで、要素リソースを同じコレクション \(<xref:System.Windows.Controls.UIElementCollection> など\) に複数回導入できます。  `x:Shared="false"` を指定しない場合は、コレクションの内容が一意であることが強制されるため、この操作が無効になります。  ただし、`x:Shared="false"` の動作は、基本的には同じインスタンスを返すのではなく、リソースの同一インスタンスを新たに作成します。  
  
 `x:Shared="false"` を指定するもう 1 つのシナリオは、アニメーションの値用に <xref:System.Windows.Freezable> リソースを使用し、そのリソースをアニメーションごとに変更する場合です。  
  
 `false` 文字列の処理では、大文字と小文字が区別されません。  
  
 WPF では、`x:Shared` は、次の条件下でのみ有効となります。  
  
-   `x:Shared` が指定された項目を含んでいる <xref:System.Windows.ResourceDictionary> をコンパイルする必要があります。  <xref:System.Windows.ResourceDictionary> を Loose XAML 内に含めたり、テーマに使用したりすることはできません。  
  
-   項目を含んでいる <xref:System.Windows.ResourceDictionary> を、別の <xref:System.Windows.ResourceDictionary> 内に入れ子にすることはできません。  たとえば、既に <xref:System.Windows.ResourceDictionary> の項目となっている <xref:System.Windows.Style> 内にある <xref:System.Windows.ResourceDictionary> 内の項目には、`x:Shared` を使用できません。  
  
## 参照  
 <xref:System.Windows.ResourceDictionary>   
 [XAML リソース](../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [基本要素](../../../docs/framework/wpf/advanced/base-elements.md)