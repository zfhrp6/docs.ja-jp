---
title: "属性に格納されている情報の取得 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性 [.NET Framework], 取得"
  - "複数の属性インスタンス"
  - "取得 (属性を)"
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 属性に格納されている情報の取得
カスタム属性を取得するプロセスは簡単です。  まず、取得する属性のインスタンスを宣言します。  次に、<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> メソッドを使用して、取得する属性の値に新しい属性を初期化します。  新しい属性が初期化されたら、そのプロパティを使用して値を取得できます。  
  
> [!IMPORTANT]
>  このトピックでは、実行コンテキストに読み込まれるコードの属性を取得する方法について説明します。  リフレクション専用のコンテキストに読み込むコードの属性を取得するには、「[方法 : リフレクションのみのコンテキストにアセンブリを読み込む](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)」に示されているように、<xref:System.Reflection.CustomAttributeData> クラスを使用する必要があります。  
  
 ここでは、属性を取得する方法について説明します。  
  
-   [属性の 1 つのインスタンスの取得。](#cpconretrievingsingleinstanceofattribute)  
  
-   [同じスコープに適用された属性の複数のインスタンスの取得。](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [他のスコープに適用された属性の複数のインスタンスの取得。](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## 属性の 1 つのインスタンスの取得  
 前のセクションで説明した `DeveloperAttribute` が、クラス レベルで `MainApp` クラスに適用されている例を次に示します。  `GetAttribute` メソッドは、**GetCustomAttribute** を使用して、`DeveloperAttribute` に格納されている値をクラス レベルで取得し、コンソールに表示します。  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 このプログラムは、実行されると次のテキストを表示します。  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 属性が見つからない場合、**GetCustomAttribute** メソッドは `MyAttribute` を null 値に初期化します。  この例では、`MyAttribute` をチェックして、属性が見つからない場合はユーザーに通知します。  クラス スコープ内に `DeveloperAttribute` が見つからない場合は、コンソールに次のメッセージが表示されます。  
  
```  
The attribute was not found.   
```  
  
 この例では、属性の定義が現在の名前空間内にあることを想定しています。  属性の定義が現在の名前空間内にないときは、属性の定義がある名前空間をインポートする必要があります。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## 同じスコープに適用された属性の複数のインスタンスの取得  
 前の例では、調べるクラスと検索する属性が <xref:System.Attribute.GetCustomAttribute%2A> に渡されています。  このコードが正常に機能するのは、属性の 1 つのインスタンスだけがクラス レベルで適用されているときです。  属性の複数のインスタンスが同じクラス レベルで適用されている場合は、**GetCustomAttribute** メソッドによってすべての情報を取得することはできません。  同じ属性の複数のインスタンスが同じスコープに適用されている場合は、<xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName> を使用して、属性のすべてのインスタンスを配列に格納できます。  たとえば、`DeveloperAttribute` の 2 つのインスタンスが同じクラスのクラス レベルで適用されている場合は、両方の属性で見つかる情報を表示するように `GetAttribute` メソッドを変更できます。  ただし、同じレベルで複数の属性を適用するには、<xref:System.AttributeUsageAttribute> で **AllowMultiple** プロパティを **true** として属性を定義しておく必要があります。  
  
 **GetCustomAttributes** メソッドを使用して、指定したクラス内の `DeveloperAttribute` のすべてのインスタンスを参照する配列を作成する方法を次のコード例に示します。  すべての属性の値は、コンソールに表示されます。  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 属性が見つからない場合、このコードはユーザーに警告を発します。  それ以外の場合は、`DeveloperAttribute` の両方のインスタンスに含まれている情報が表示されます。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## ほかのスコープに適用された属性の複数のインスタンスの取得  
 <xref:System.Attribute.GetCustomAttributes%2A> メソッドと <xref:System.Attribute.GetCustomAttribute%2A> メソッドでは、クラス全体を検索してクラス内の属性のすべてのインスタンスを返すことはできません。  これらのメソッドが一度に検索するのは、指定された 1 つのメソッドまたは 1 つのメンバーだけです。  クラスのメンバーすべてに同じ属性が適用されていて、それらのメンバーに適用されたすべての属性の値を取得するには、すべてのメソッドやメンバーを個別に **GetCustomAttributes** と **GetCustomAttribute** に渡す必要があります。  
  
 パラメーターとしてクラスをとり、そのクラス レベルとそのクラスの各メソッドすべてについて `DeveloperAttribute` \(前に定義されています\) を検索するコード例を次に示します。  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 メソッド レベルまたはクラス レベルで `DeveloperAttribute` のインスタンスが見つからない場合、`GetAttribute` メソッドは属性が見つからなかったことをユーザーに通知し、属性が含まれないメソッド名またはクラス名を表示します。  属性が見つかった場合は、`Name`、`Level`、`Reviewed` の各フィールドがコンソールに表示されます。  
  
 渡されたクラス内の各メソッドとメンバーを取得するには、<xref:System.Type> クラスのメンバーを使用します。  この例では、最初に **Type** オブジェクトを問い合わせて、クラス レベルの属性情報を取得しています。  次に、<xref:System.Type.GetMethods%2A?displayProperty=fullName> を使用して、すべてのメソッドのインスタンスを <xref:System.Reflection.MemberInfo?displayProperty=fullName> オブジェクトの配列に格納し、メソッド レベルの属性情報を取得します。  また、<xref:System.Type.GetProperties%2A?displayProperty=fullName> メソッドを使用してプロパティ レベルの属性を調べることも、<xref:System.Type.GetConstructors%2A?displayProperty=fullName> メソッドを使用してコンストラクター レベルの属性を調べることもできます。  
  
## 参照  
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName>   
 [属性](../../../docs/standard/attributes/index.md)