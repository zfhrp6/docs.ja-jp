---
title: ".NET Framework のジェネリック コレクション | Microsoft Docs"
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
  - "ジェネリック コレクション [.NET Framework]"
  - "ジェネリック [.NET Framework], コレクション"
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# .NET Framework のジェネリック コレクション
このトピックでは、.NET Framework のジェネリック コレクション クラスとその他のジェネリック型について概説します。  
  
## .NET Framework のジェネリック コレクション  
 .NET Framework クラス ライブラリでは、<xref:System.Collections.Generic> および <xref:System.Collections.ObjectModel> の名前空間に多数のジェネリック コレクション クラスが用意されています。  これらのクラスについて詳しくは、「[一般的に使用されるコレクション型](../../../docs/standard/collections/commonly-used-collection-types.md)」を参照してください。  
  
### System.Collections.Generic  
 ジェネリック コレクション型の多くは、非ジェネリック型に直接類似しています。  <xref:System.Collections.Generic.Dictionary%602> は、<xref:System.Collections.Hashtable> のジェネリック バージョンです。これは列挙体のために <xref:System.Collections.DictionaryEntry> ではなくジェネリック構造体 <xref:System.Collections.Generic.KeyValuePair%602> を使用します。  
  
 <xref:System.Collections.Generic.List%601> は <xref:System.Collections.ArrayList> のジェネリック バージョンです。  ジェネリックの <xref:System.Collections.Generic.Queue%601> および <xref:System.Collections.Generic.Stack%601> クラスには、非ジェネリックのバージョンに対応するものがあります。  
  
 <xref:System.Collections.Generic.SortedList%602> には、ジェネリックおよび非ジェネリックのバージョンがあります。  どちらのバージョンも、ディクショナリとリストのハイブリッドです。  <xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラスは純粋なディクショナリであり、対応する非ジェネリックのバージョンはありません。  
  
 <xref:System.Collections.Generic.LinkedList%601> ジェネリック クラスは、実際のリンク リストです。  これには、対応する非ジェネリックのバージョンはありません。  
  
### System.Collections.ObjectModel  
 <xref:System.Collections.ObjectModel.Collection%601> ジェネリック クラスは、独自のジェネリック コレクション型を派生させるための基本クラスを提供します。  <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> クラスは、<xref:System.Collections.Generic.IList%601> ジェネリック インターフェイスを実装する任意の型から、読み取り専用のコレクションを生成するための簡単な方法を提供します。  <xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスは、独自のキーを含むオブジェクトを格納するための方法を提供します。  
  
## その他のジェネリック型  
 <xref:System.Nullable%601> ジェネリック構造体により、`null` が割り当て可能であるかのように値型を使用できます。  これは、値型が含まれるフィールドが欠落している可能性のあるデータベース クエリで作業するときに便利です。  ジェネリック型パラメーターには、任意の値型を指定できます。  
  
> [!NOTE]
>  C\# には null 許容型の構文があるので、その言語では <xref:System.Nullable%601> を明示的に使用する必要はありません。  
  
 <xref:System.ArraySegment%601> ジェネリック構造体は、任意の型の 0 から始まる 1 次元の配列内で、要素の範囲を区切る方法を提供します。  ジェネリック型パラメーターは、配列の要素の型です。  
  
 <xref:System.EventHandler%601> ジェネリック デリゲートにより、イベントが [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] によって使用されるイベント処理パターンに従う場合に、イベントを処理するためにデリゲート型を宣言する必要がなくなります。  たとえば、イベントのデータを保持するために、<xref:System.EventArgs> から派生した `MyEventArgs` クラスを作成したとします。  その場合、イベントを次のように宣言できます。  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## 参照  
 <xref:System.Collections.Generic?displayProperty=fullName>   
 <xref:System.Collections.ObjectModel?displayProperty=fullName>   
 [ジェネリック](../../../docs/standard/generics/index.md)   
 [配列とリストの操作に使用する汎用デリゲート](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)   
 [ジェネリック インターフェイス](../../../docs/standard/generics/interfaces.md)