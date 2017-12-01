---
title: "属性に格納されている情報の取得"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d3fd9a5a49d65b37d2cdb5107e9c516a6df5847
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-information-stored-in-attributes"></a>属性に格納されている情報の取得
簡単なプロセスは、カスタム属性を取得します。 最初に、取得する属性のインスタンスを宣言します。 次に、使用、<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>新しい属性を取得する属性の値を初期化します。 新しい属性が初期化されると、単にそのプロパティを使用する値を取得します。  
  
> [!IMPORTANT]
>  このトピックでは、実行コンテキストに読み込まれるコードの属性を取得する方法について説明します。 リフレクション専用コンテキストに読み込まれるコードの属性を取得するには、使用する必要があります、<xref:System.Reflection.CustomAttributeData>クラスのように[する方法: リフレクション コンテキストにアセンブリをロード](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)です。  
  
 このセクションでは、次の属性を取得する方法について説明します。  
  
-   [属性の 1 つのインスタンスを取得します。](#cpconretrievingsingleinstanceofattribute)  
  
-   [同じスコープに適用される属性の複数のインスタンスを取得します。](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [他のスコープに適用される属性の複数のインスタンスを取得します。](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>属性の 1 つのインスタンスを取得します。  
 次の例で、 `DeveloperAttribute` (前のセクションで説明) に適用される、`MainApp`クラス レベルのクラスです。 `GetAttribute`メソッドを使用**されていて**に格納されている値を取得する`DeveloperAttribute`それらをコンソールに表示する前にクラス レベル上。  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 このプログラムは、実行時に、次のテキストを表示します。  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 属性が見つからない場合、**されていて**メソッド初期化`MyAttribute`を null 値にします。 この例で確認`MyAttribute`このようなインスタンスの属性が見つからない場合、ユーザーに通知します。 場合、`DeveloperAttribute`はクラス スコープで、次のメッセージをコンソールに表示します。  
  
```  
The attribute was not found.   
```  
  
 この例では、属性の定義が、現在の名前空間にある前提としています。 現在の名前空間がない場合、属性の定義が存在する名前空間をインポートしてください。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>同じスコープに適用される属性の複数のインスタンスを取得します。  
 前の例では、検査するクラスとを検索する特定の属性に渡されるの<xref:System.Attribute.GetCustomAttribute%2A>します。 そのコードは、属性の 1 つのインスタンスは、クラス レベルで適用されても専用の場合は動作します。 ただし、同じクラス レベルでは、属性の複数のインスタンスが適用されている場合、**されていて**メソッドがすべての情報を取得できません。 使用できる場合は、同じ属性の複数のインスタンスが同じスコープに適用されます、<xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>配列属性のすべてのインスタンスを配置します。 たとえば、次の 2 つのインスタンス`DeveloperAttribute`、同じクラスのクラス レベルで適用される、`GetAttribute`メソッドは、両方の属性に含まれる情報を表示するように変更できます。 ただし、同じレベルでは、複数の属性を適用すると属性を定義する必要があります、 **AllowMultiple**プロパティに設定**true**で、<xref:System.AttributeUsageAttribute>です。  
  
 次のコード例を使用する方法を示しています、 **GetCustomAttributes**メソッドのすべてのインスタンスを参照している配列を作成する`DeveloperAttribute`いずれかでクラスを指定します。 すべての属性の値は、コンソールに表示されます。  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 属性が見つからない場合、このコードをユーザーに通知します。 両方のインスタンスにそれ以外の場合、情報が含まれている`DeveloperAttribute`が表示されます。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>他のスコープに適用される属性の複数のインスタンスを取得します。  
 <xref:System.Attribute.GetCustomAttributes%2A>と<xref:System.Attribute.GetCustomAttribute%2A>メソッドせずクラス全体を検索してそのクラスの属性のすべてのインスタンスを返します。 代わりが指定されたメソッドまたはメンバーを 1 つだけを同時に検索します。 すべてのメソッドまたはメンバーに個別に指定する必要がありますすべてのメンバーに適用される同じ属性を持つクラスがあるし、それらのメンバーに適用されるすべての属性の値を取得する、 **GetCustomAttributes**と**されていて**です。  
  
 次のコード例は、パラメーターとしてクラスを受け取りし、検索、 `DeveloperAttribute` (定義されている以前) とそのクラスの各メソッドはすべて、クラス レベルでします。  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 インスタンスがない場合、`DeveloperAttribute`メソッド レベルまたはクラス レベル上にある、`GetAttribute`メソッドは、属性が見つかりましたがないユーザーに通知し、メソッドまたは属性が含まれていないクラスの名前を表示します。 属性が見つかった場合、 `Name`、 `Level`、および`Reviewed`フィールドがコンソールに表示されます。  
  
 メンバーを使用することができます、<xref:System.Type>クラスを渡されたクラスで、個々 のメソッドとメンバーを取得します。 この例の最初のクエリ、**型**クラス レベルの属性情報を取得するオブジェクト。 次に、使用して<xref:System.Type.GetMethods%2A?displayProperty=nameWithType>を配列のすべてのメソッドのインスタンスを配置する<xref:System.Reflection.MemberInfo?displayProperty=nameWithType>メソッド レベルの属性情報を取得するオブジェクト。 使用することも、<xref:System.Type.GetProperties%2A?displayProperty=nameWithType>プロパティ レベルの属性を確認するメソッドまたは<xref:System.Type.GetConstructors%2A?displayProperty=nameWithType>コンス トラクターのレベルの属性を確認します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [属性](../../../docs/standard/attributes/index.md)
