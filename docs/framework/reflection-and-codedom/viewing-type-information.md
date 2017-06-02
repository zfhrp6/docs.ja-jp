---
title: "型情報の表示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "リフレクション, 表示 (型情報を)"
  - "Type オブジェクト"
  - "型, 表示 (型情報を)"
  - "表示 (型情報を)"
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 型情報の表示
<xref:System.Type?displayProperty=fullName> クラスは、リフレクションの中枢です。  リフレクションが **Type** の作成を要求すると、共通言語ランタイムは、読み込まれた型に対して **Type** オブジェクトを作成します。  **Type** オブジェクトのメソッド、フィールド、プロパティ、および入れ子クラスを使用すると、その型についてのすべての情報を調べることができます。  
  
 まだ読み込まれていないアセンブリから **Type** オブジェクトを取得するには、<xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> または <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> を使用し、必要な型の名前を 1 つ以上渡します。  既に読み込まれているアプリケーションから **Type** オブジェクトを取得するには、<xref:System.Type.GetType%2A?displayProperty=fullName> を使用します。  モジュールの **Type** オブジェクトを取得するには、<xref:System.Reflection.Module.GetType%2A?displayProperty=fullName> および <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName> を使用します。  
  
> [!NOTE]
>  ジェネリック型およびメソッドを調べたり操作したりする場合は、「[リフレクションとジェネリック型](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)」および「[方法 : リフレクションを使用してジェネリック型をチェックおよびインスタンス化する](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)」を参照してください。  
  
 アセンブリの <xref:System.Reflection.Assembly> オブジェクトおよびモジュールを取得するための構文を示すコード例は、次のとおりです。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 既に読み込まれているアセンブリから **Type** オブジェクトを取得する例を次に示します。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 **Type** を取得した後は、さまざまな方法で、この型のメンバーに関する情報を探索できます。  たとえば、現在の型の各メンバーが記述されている <xref:System.Reflection.MemberInfo> オブジェクトの配列を取得する <xref:System.Type.GetMembers%2A?displayProperty=fullName> メソッドを呼び出すと、その型のすべてのメンバーについて調べることができます。  
  
 また、**Type** クラスのメソッドを使用し、名前を指定することで、1 つ以上のコンストラクター、メソッド、イベント、フィールド、またはプロパティについての情報を取得できます。  たとえば、<xref:System.Type.GetConstructor%2A?displayProperty=fullName> は、現在のクラスの特定のコンストラクターをカプセル化します。  
  
 **Type** が存在する場合は、<xref:System.Type.Module%2A?displayProperty=fullName> プロパティを使用して、その型を含んでいるモジュールをカプセル化するオブジェクトを取得できます。  そのモジュールを含んでいるアセンブリをカプセル化するオブジェクトを検索するには、<xref:System.Reflection.Module.Assembly%2A?displayProperty=fullName> プロパティを使用します。  <xref:System.Type.Assembly%2A?displayProperty=fullName> プロパティを使用すると、型をカプセル化するアセンブリを直接取得できます。  
  
## System.Type および ConstructorInfo  
 特定のクラスのコンストラクター \(ここでは <xref:System.String> クラスのコンストラクター\) を一覧する方法を次の例で示します。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## MemberInfo、MethodInfo、FieldInfo、および PropertyInfo  
 <xref:System.Reflection.MemberInfo>、<xref:System.Reflection.MethodInfo>、<xref:System.Reflection.FieldInfo>、または <xref:System.Reflection.PropertyInfo> の各オブジェクトを使用して、型のメソッド、プロパティ、イベント、およびフィールドについての情報を取得します。  
  
 **MemberInfo** を使用して **System.IO.File** クラスのメンバー数を一覧し、[System.Type.IsPublic](frlrfSystemTypeClassIsPublicTopic) プロパティを使用して、このクラスの参照範囲を確認する例を次に示します。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 特定のメンバーの型を調べる例を次に示します。  **MemberInfo** クラスのメンバーに対してリフレクションを実行し、そのメンバーの型を一覧します。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 すべてのリフレクション **\*Info** クラスを <xref:System.Reflection.BindingFlags> と共に使用して、指定したクラスのすべてのメンバー \(コンストラクター、フィールド、プロパティ、イベント、およびメソッド\) を一覧し、メンバーを静的カテゴリとインスタンス カテゴリに分割する例を次に示します。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## 参照  
 <xref:System.Reflection.BindingFlags>   
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.GetMembers%2A?displayProperty=fullName>   
 <xref:System.Type.GetFields%2A?displayProperty=fullName>   
 <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>   
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName>   
 <xref:System.Reflection.MemberInfo>   
 <xref:System.Reflection.ConstructorInfo>   
 <xref:System.Reflection.MethodInfo>   
 <xref:System.Reflection.FieldInfo>   
 <xref:System.Reflection.EventInfo>   
 <xref:System.Reflection.ParameterInfo>   
 [リフレクションとジェネリック型](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)