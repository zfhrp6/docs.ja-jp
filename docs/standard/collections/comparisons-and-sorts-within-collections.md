---
title: "コレクション内での比較と並べ替え | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0da0bed43cb7871f522b94b134afb164d8ee3ab5
ms.lasthandoff: 04/18/2017

---
# <a name="comparisons-and-sorts-within-collections"></a>コレクション内での比較と並べ替え
<xref:System.Collections> クラスは、削除する要素を検索するか、キーと値のペアの値を返すかに関係なく、コレクションの管理に関連するほぼすべての処理において比較を実行します。  
  
 通常、コレクションは等値比較子か順序比較子、またはその両方を使用します。 比較には 2 つのコンストラクターが使用されます。  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>等価性のチェック  
 `Contains`、<xref:System.Collections.IList.IndexOf%2A>、<xref:System.Collections.Generic.List%601.LastIndexOf%2A>、`Remove` のようなメソッドでは、コレクション要素に等値比較子が使用されます。 コレクションがジェネリックの場合、次のガイドラインに従ってアイテムの等価性が比較されます。  
  
-   T 型で <xref:System.IEquatable%601> ジェネリック インターフェイスが実装されている場合、等値比較子はそのインターフェイスの <xref:System.IEquatable%601.Equals%2A> メソッドです。  
  
-   T 型で <xref:System.IEquatable%601> が実装されない場合、<xref:System.Object.Equals%2A?displayProperty=fullName> が使用されます。  
  
 また、ディクショナリ コレクションの一部のコンストラクター オーバーロードでは、<xref:System.Collections.Generic.IEqualityComparer%601> 実装が受け取られ、これを使用してキーの等価性が比較されます。 例については、<xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=fullName> コンストラクターをご覧ください。  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>並べ替え順序の決定  
 `BinarySearch`、`Sort` などのメソッドは、コレクション要素に対して順序比較子を使用します。 コレクションの要素間または要素と指定された値との間で比較を実行できます。 オブジェクトの比較には、`default comparer`と`explicit comparer`の概念が適用されます。  
  
 既定の比較子は、比較される 1 つ以上のオブジェクトに依存して **IComparable** インターフェイスを実装します。 リスト コレクションの値として使用されるか、またはディクショナリ コレクションのキーとして使用されるすべてのクラスで、**IComparable** を実装することをお勧めします。 ジェネリック コレクションの場合、等価比較は次の基準に従って決定されます。  
  
-   T 型で <xref:System.IComparable%601?displayProperty=fullName> ジェネリック インターフェイスが実装される場合、既定の比較子はそのインターフェイスの <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=fullName> メソッドです。  
  
-   T 型で非ジェネリックの <xref:System.IComparable?displayProperty=fullName> インターフェイスが実装される場合、既定の比較子はそのインターフェイスの <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=fullName> メソッドです。  
  
-   T 型でいずれのインターフェイスも実装されていない場合、既定の比較子は存在せず、比較子または比較デリゲートを明示的に指定する必要があります。  
  
 明示的な比較を指定するために、一部のメソッドではパラメーターとして **IComparer** 実装を受け取ります。 たとえば、<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=fullName> メソッドは <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> 実装を受け取ります。  
  
 システムの現在のカルチャ設定は、コレクション内の比較と並べ替えに影響を与える可能性があります。 既定では、**Collections** クラスの比較と並べ替えはカルチャに依存します。 カルチャ設定を無視し、一貫性のある比較結果と並べ替え結果を得るには、<xref:System.Globalization.CultureInfo> を受け取るメンバー オーバーロードと共に <xref:System.Globalization.CultureInfo.InvariantCulture%2A> を使用します。 詳細については、「[カルチャを認識しないコレクションの操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)」と「[カルチャを認識しない配列の操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)」を参照してください。  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>等価性と並べ替えの例  
 次のコードは、単純なビジネス オブジェクトでの <xref:System.IEquatable%601> と <xref:System.IComparable%601> の実装を示しています。 また、オブジェクトがリストに格納され、並べ替えられている場合、<xref:System.Collections.Generic.List%601.Sort> メソッドを呼び出すと、結果的に `Part` 型の既定の比較子と、匿名メソッドを使用して実装された <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> メソッドを使用することになります。  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.IComparer>   
 <xref:System.IEquatable%601>   
 <xref:System.Collections.Generic.IComparer%601>   
 <xref:System.IComparable>   
 <xref:System.IComparable%601>
