---
title: "方法 : リフレクションのみのコンテキストにアセンブリを読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework], 読み込み (リフレクション)"
  - "アセンブリ [.NET Framework], リフレクションのみのローダー コンテキスト"
  - "属性 [.NET Framework], 取得"
  - "リフレクション, リフレクションのみのローダー コンテキスト"
  - "リフレクションのみのローダー コンテキスト"
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : リフレクションのみのコンテキストにアセンブリを読み込む
リフレクションのみの読み込みのコンテキストでは、他のプラットフォームや .NET Framework の他のバージョン用にコンパイルされたアセンブリをチェックできます。  このコンテキストに読み込まれたコードはチェックのみ可能で、実行できません。  そのため、コンストラクターを実行できないので、オブジェクトは作成できません。  また、コードを実行できないため、依存関係は自動的には読み込まれません。  依存関係をチェックする必要がある場合は、依存関係を独自に読み込む必要があります。  
  
### アセンブリをリフレクションのみの読み込みのコンテキストに読み込むには  
  
1.  表示名が指定されたアセンブリを読み込むには、<xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> メソッド オーバーロードを使用し、パスが指定されたアセンブリを読み込むには、<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> メソッドを使用します。  アセンブリがバイナリ イメージの場合は、[ReflectionOnlyLoad\(Byte\<xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> メソッド オーバーロードを使用します。  
  
    > [!NOTE]
    >  リフレクションのみのコンテキストを使用して、実行コンテキストのバージョン以外の .NET Framework のバージョンから mscorlib.dll のバージョンを読み込むことはできません。  
  
2.  アセンブリに依存関係がある場合、<xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> メソッドは依存関係を読み込みません。  依存関係をチェックする場合は、依存関係を独自に読み込む必要があります。  
  
3.  アセンブリの <xref:System.Reflection.Assembly.ReflectionOnly%2A> プロパティを使用して、アセンブリをリフレクションのみのコンテキストに読み込むかどうかを決定します。  
  
4.  アセンブリまたはアセンブリ内の型に属性が適用されている場合は、<xref:System.Reflection.CustomAttributeData> クラスを使用してこれらの属性をチェックし、リフレクションのみのコンテキストでコードが実行されないことを確認します。  <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=fullName> メソッドの適切なオーバーロードを使用して、アセンブリ、メンバー、またはパラメーターに適用されている属性を表す <xref:System.Reflection.CustomAttributeData> オブジェクトを取得します。  
  
    > [!NOTE]
    >  アセンブリまたはそのコンテンツに適用されている属性はそのアセンブリで定義されていることもありますし、リフレクションのみのコンテキストに読み込まれた別のアセンブリで定義されていることもあります。  属性がどこで定義されているかを事前に確認する方法はありません。  
  
## 使用例  
 リフレクションのみのコンテキストに読み込まれたアセンブリに適用されている属性をチェックする方法を以下のコード例に示します。  
  
 このコード例では、2 つのコンストラクターと 1 つのプロパティでカスタム属性を定義します。  この属性は、アセンブリ、アセンブリで宣言された型、型のメソッド、およびメソッドのパラメーターに適用されます。  このコード例を実行すると、アセンブリがそれ自体をリフレクションのみのコンテキストに読み込み、アセンブリとそれに含まれている型およびメンバーに適用されているカスタム属性に関する情報を表示します。  
  
> [!NOTE]
>  コード例を簡素にするために、アセンブリがそれ自体を読み込んでチェックします。  通常、同じアセンブリが実行コンテキストとリフレクションのみのコンテキストの両方に読み込まれることはありません。  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## 参照  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>   
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>   
 <xref:System.Reflection.CustomAttributeData>