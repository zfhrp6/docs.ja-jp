---
title: "Hashtable コレクション型と Dictionary コレクション型"
description: "Hashtable コレクション型と Dictionary コレクション型"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0f18fac7-fd0d-4f25-a046-1d3d51de062e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 58c87f9e86b5b97feb654e92a56f81940c201a6a
ms.lasthandoff: 03/02/2017

---

# <a name="hashtable-and-dictionary-collection-types"></a>Hashtable コレクション型と Dictionary コレクション型

[System.Collections.Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) クラスと、[System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) および [System.Collections.Concurrent.ConcurrentDictionary<T>](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) ジェネリック クラスは、[System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) インターフェイスを実装します。 `Dictionary<T>` ジェネリック クラスも、[IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2) ジェネリック インターフェイスを実装します。 そのため、これらのコレクション内の各要素は、キーと値のペアになります。

`Hashtable` オブジェクトは、コレクションの要素を含むバケットので構成されます。 バケットは`Hashtable` に含まれる要素の仮想サブグループで、これを使用することにより、ほとんどのコレクションで検索と取得がより簡単で高速になります。 各バケットは、ハッシュ関数を使用して生成され、要素のキーに基づいている、ハッシュ コードに関連付けられています。

ジェネリック [HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1) クラスは、一意の要素を格納するための順序付けられていないコレクションです。 

ハッシュ関数は、キーに基づく数値のハッシュ コードを返すアルゴリズムです。 キーは、格納されているオブジェクトのいくつかのプロパティの値です。 ハッシュ関数は、同じキーに対して常に同じハッシュ コードを返す必要があります。 ハッシュ関数によって&2; つの異なるキーを持つ同一のハッシュ コードを生成することも可能ですが、一意のキーごとに一意のハッシュ コードを生成するハッシュ関数のほうが、ハッシュ テーブルから要素を取得する際により優れたパフォーマンスを実現します。

`Hashtable` で要素として使用されている各オブジェクトは、`GetHashCode` メソッドの実装を使用して、それ自体のハッシュ コードを生成できる必要があります。 

オブジェクトは、`Hashtable` に追加されるとき、そのオブジェクトのハッシュ コードと一致するハッシュ コードに関連付けられたバケットに格納されます。 値が `Hashtable` 内で検索されるとき、その値のハッシュ コードが生成されて、そのハッシュ コードに関連付けられたバケットが検索されます。

たとえば、文字列のハッシュ関数は、文字列内の各文字の ASCII コードを取得し、それらを加え合わせて&1; つのハッシュ コードを生成することができます。 その場合、文字列「picnic」のハッシュ コードは文字列「basket」のハッシュ コードと異なるので、文字列「picnic」と「basket」は異なるバケットに格納されます。 それに対して、「stressed」と「desserts」は同じハッシュ コードを持つので、同じバケットに格納されます。

`Dictionary<T>` および `ConcurrentDictionary<T>` クラスには、`Hashtable` クラスと同じ機能があります。 特定の型 (`Object` を除く) の`Dictionary<T>` は、値型の `Hashtable` よりも優れたパフォーマンスを実現します。 これは、`Hashtable` の要素の型が `Object` であるため、値型を格納したり取得したりすると、ボックス化とボックス化解除が通常発生するためです。 複数のスレッドが同時にコレクションにアクセスするときには、`ConcurrentDictionary<T>` クラスを使用する必要があります。

## <a name="see-also"></a>関連項目

[Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable)

[IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)

[Dictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2)

[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)

[System.Collections.Concurrent.ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2)

[一般的に使用されるコレクション型](commonly-used-collection-types.md)


