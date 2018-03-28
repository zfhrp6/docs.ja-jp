---
title: ref 戻り値と ref ローカル変数 (C# ガイド)
description: ref 戻り値と ref ローカル変数を定義して使用する方法について説明します。
author: rpetrusha
ms.author: ronpet
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: c37c6dd61ae02813bcc467982f3b175da9136e4a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="ref-returns-and-ref-locals"></a>ref 戻り値と ref ローカル変数

C# 7 以降の C# は参照戻り値 (ref 戻り値) に対応しています。 参照戻り値を使用すると、メソッドから呼び出し元に、値ではなく、変数への参照を返すことができます。 呼び出し元は、返された変数を値渡しとして処理するか、参照渡しとして処理するかを選択できます。 呼び出し元は、それ自体が、返された値の参照である新しい変数を作成できます。これは ref ローカルと呼ばれています。

## <a name="what-is-a-reference-return-value"></a>参照戻り値とは

呼び出されたメソッドに参照によって引数を渡す*参照渡し*は、ほとんどの開発者によく知られています。 呼び出されたメソッドの引数リストに参照によって渡された変数が含まれており、呼び出されたメソッドが値に加えた変更は呼び出し元に認識されます。 *参照戻り値*とは、ある変数の範囲にメソッドが含まれ、その変数の有効期間がメソッドの戻りより長いとき、その変数にメソッドが*参照* (エイリアス) を返すことを意味します。 呼び出し元によるメソッドの戻り値の変更は、メソッドによって返される変数に対して行われます。

メソッドが*参照戻り値*を返すという宣言があれば、それはそのメソッドが変数にエイリアスを返すことを示します。 この設計の意図は、多くの場合、呼び出し元のコードが変数の変更などを行うとき、そのコードにはエイリアス経由でその変数にアクセスさせるというものです。 参照で返すメソッドには戻り値の型 `void` を与えることができません。

メソッドが参照戻り値として返すことができる式には、いくつかの制限があります。 次の設定があります。

- 戻り値の有効期間は、メソッドの実行より長くならないようにする必要があります。 言い換えると、値を返すメソッドに含まれているローカル変数にすることはできません。 クラスのインスタンスまたは静的フィールドを戻り値にすることができます。または、メソッドに渡される引数を戻り値にすることもできます。 ローカル変数を返そうとすると、コンパイラ エラー CS8168 "ローカル変数 'obj' は ref ローカル変数ではないため、参照渡しで返すことはできません" が生成されます。

- 戻り値はリテラル `null` にすることができません。 `null` を返そうとすると、コンパイラ エラー CS8156 "参照渡しで返すことができないため、このコンテキストで使用できない式があります" が生成されます。

   ref 戻りを含むメソッドは、現在の値が null (インスタンス化されていない) 値か、値の型が [null 許容型](../nullable-types/index.md)の変数にエイリアスを返すことができます。
 
- 戻り値は、定数、列挙型のメンバー、プロパティの値渡し戻り値、`class` または `struct` のメソッドにすることができません。 それらのいずれかを返そうとすると、コンパイラ エラー CS8156 "参照渡しで返すことができないため、このコンテキストで使用できない式があります" が生成されます。

さらに、非同期メソッドは、実行が完了する前にまだ戻り値が判明していないときに返される可能性があるため、非同期メソッドでは参照戻り値を使用できません。
 
## <a name="defining-a-ref-return-value"></a>ref 戻り値の定義

戻り値を定義するには、メソッド シグネチャの戻り値の型に [ref](../../language-reference/keywords/ref.md) キーワードを追加します。 たとえば、次のシグネチャは、`GetContactInformation` プロパティが `Person` オブジェクトへの参照を呼び出し元に返すことを示しています。

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

さらに、メソッド本文の各 [return](../../language-reference/keywords/return.md) ステートメントによって返されるオブジェクトの名前の前に、[ref](../../language-reference/keywords/ref.md) キーワードが必要です。 たとえば、次の `return` ステートメントは、`p` という名前の `Person` オブジェクトに参照を返します。

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>ref 戻り値の使用

ref 戻り値は、呼び出されるメソッドの範囲で、別の変数のエイリアスになります。 ref 戻り値の使用は、それが別名を与える変数の使用として解釈できます。

- その値を割り当てるとき、それが別名を与える変数に値を割り当てることになります。
- その値を読み取るとき、それが別名を与える変数の値を読み取ることになります。
- *参照渡し*で値を返す場合、その同じ変数にエイリアスを返すことになります。
- *参照渡し*で別のメソッドに値を渡す場合、それが別名を与える変数に参照を渡すことになります。
- [ref ローカル](#ref-local)をエイリアスにすると、同じ変数に新しいエイリアスが作られます。


## <a name="ref-locals"></a>ref ローカル変数

`GetContactInformation` メソッドが ref 戻り値として宣言されているとします。

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

値渡し代入によって、変数の値が読み取られ、それが新しい変数に渡されます。

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

先の代入では、ローカル変数として `p` が宣言されています。 その初期値は、`GetContactInformation` によって返された値の読み取りからコピーされます。 今後、`p` に値が代入されることで、`GetContactInformation` によって返された変数の値が変わることはありません。 変数 `p` は、返された変数のエイリアスではなくなります。

*ref ローカル*変数を宣言し、元の値にエイリアスをコピーします。 次の代入では、`p` は、`GetContactInformation` から返された変数のエイリアスになります。

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

この後 `p` を使用することは、`GetContactInformation` によって返された変数を使用することと同じです。`p` はその変数のエイリアスであるためです。 `p` を変更すると、`GetContactInformation` から返される変数も変更されます。

なお、`ref` キーワードは、ローカル変数宣言の前*および*メソッド呼び出しの前の両方で使用します。 

同じ方法で、参照渡しの値にアクセスできます。 場合によっては、参照渡しの値へのアクセスによって負荷がかかる可能性があるコピー操作が回避され、パフォーマンスが向上します。 たとえば、次のステートメントは、値の参照に使用される ref ローカル値をどのように定義できるかを示しています。

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

なお、`ref` キーワードは、ローカル変数宣言の前*および* 2 番目の例の値の前で使用します。 両方の例の、変数宣言と代入の両方の `ref` キーワードを含めないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。 
 
## <a name="ref-returns-and-ref-locals-an-example"></a>ref 戻り値と ref ローカル変数: 使用例

次の例では、整数値の配列を格納する `NumberStore` クラスを定義しています。 `FindNumber` メソッドは、引数として渡された数値に等しいかそれより大きい最初の数値を参照渡しで返します。 引数に等しいかそれより大きい数値がない場合、メソッドはインデックス 0 の数値を返します。 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

次の例では、`NumberStore.FindNumber` メソッドを呼び出して、16 に等しいかそれより大きい最初の値を取得します。 呼び出し元は、メソッドによって返された値を 2 倍にします。 この変更は、次の例の出力に示されているように、`NumberStore` インスタンスの配列要素の値に反映されます。

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

参照戻り値がサポートされていない場合、このような操作は通常、配列要素のインデックスと値を返すことによって実行されます。 呼び出し元はこのインデックスを使用して、別のメソッド呼び出しで値を変更できます。 一方、インデックスを変更して配列の他の値にアクセスし、変更することも可能です。  
 
## <a name="see-also"></a>関連項目

[ref キーワード](../../language-reference/keywords/ref.md)  
[値の型による参照セマンティクス](../../../csharp/reference-semantics-with-value-types.md)
