---
title: "Collection Initializers (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.CollectionInitializer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "collection initializers [Visual Basic]"
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# Collection Initializers (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*コレクション初期化子*は、コレクションを作成し、そのコレクションに初期値を設定するための簡略された構文を提供します。  コレクション初期化子は、コレクションを既知の値のセットから作成する場合に便利です。値のセットの例として、メニュー オプションやカテゴリのリスト、数値の初期セット、曜日や月の名前の静的文字列のリスト、検証に使用する都道府県リストなどの地理的な場所が挙げられます。  
  
 コレクションの詳細については、「[コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 コレクション初期化子は、`From` キーワードの後に中かっこ \(`{}`\) を使用して指定します。  この構文は、「[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)」に説明されている配列リテラル構文に似ています。  コレクションの作成のためにコレクション初期化子を使用する各種の方法を次の例に示します。  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_1.vb)]  
  
> [!NOTE]
>  C\# にも、コレクション初期化子があります。  C\# のコレクション初期化子の機能は、Visual Basic のコレクション初期化子の機能と同じです。  C\# のコレクション初期化子の詳細については、「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。  
  
## 構文  
 コレクション初期化子は、次のコードに示すように、`From` キーワードの後に、コンマ区切りの値を中かっこ \(`{}`\) で囲んだリストから構成されます。  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_2.vb)]  
  
 <xref:System.Collections.Generic.List%601> や <xref:System.Collections.Generic.Dictionary%602> などのコレクションを作成する場合、次のコードに示すように、コレクション初期化子の前にコレクション型を指定する必要があります。  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_3.vb)]  
  
> [!NOTE]
>  コレクション初期化子とオブジェクト初期化子を組み合わせて、同じコレクション オブジェクトを初期化することはできません。  オブジェクト初期化子を使用して、コレクション初期化子内のオブジェクトを初期化できます。  
  
## コレクション初期化子を使用したコレクションの作成  
 コレクション初期化子を使用してコレクションを作成する場合、コレクション初期化子に指定された各値は、コレクションの該当する `Add` メソッドに渡されます。  たとえば、コレクション初期化子を使用して <xref:System.Collections.Generic.List%601> を作成する場合、コレクション初期化子の各文字列値は、<xref:System.Collections.Generic.List%601.Add%2A> メソッドに渡されます。  コレクション初期化子を使用してコレクションを作成する場合、指定する型は、有効なコレクション型である必要があります。  有効なコレクション型の例には、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するクラスや、<xref:System.Collections.CollectionBase> クラスを継承するクラスなどがあります。  指定する型は、次の条件を満たす `Add` メソッドを公開する必要もあります。  
  
-   `Add` メソッドは、コレクション初期化子の呼び出し元の範囲から使用できる必要があります。  コレクションの非パブリック メソッドにアクセスできるシナリオでコレクション初期化子を使用する場合、`Add` メソッドはパブリックである必要はありません。  
  
-   `Add` メソッドは、コレクション クラスのインスタンス メンバーまたは `Shared` メンバーであるか、拡張メソッドである必要があります。  
  
-   オーバーロード解決規則に基づいて、コレクション初期化子で提供される型に対応付けることができる `Add` メソッドが存在する必要があります。  
  
 例として、コレクション初期化子を使用して `List(Of Customer)` コレクションを作成する方法を次のコード例に示します。  コードの実行時、各 `Customer` オブジェクトはジェネリック リストの `Add(Customer)` メソッドに渡されます。  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_4.vb)]  
  
 次のコード例に、同等の内容でコレクション初期化子を使用しない方法を示します。  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_5.vb)]  
  
 `Customer` オブジェクトのコンストラクターと一致するパラメーターがある `Add` メソッドがコレクションにある場合、次のセクションで説明するように、`Add` メソッドのパラメーター値は、コレクション初期化子内で入れ子にすることができます。  コレクションに `Add` メソッドがない場合、拡張メソッドとしてメソッドを作成できます。  コレクションに拡張メソッドとして `Add` メソッドを作成する方法の例については、「[How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)」を参照してください。  コレクション初期化子内で使用できるカスタム コレクションを作成する方法の例については、「[How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)」を参照してください。  
  
## 入れ子になったコレクション初期化子  
 作成するコレクションの `Add` メソッドの固有のオーバーロードを識別するため、コレクション初期化子内の値を入れ子にすることができます。  `Add` メソッドに渡される値は、配列リテラルやコレクション初期化子に指定する場合と同様に、コンマ区切りにして中かっこ \(`{}`\) で囲む必要があります。  
  
 入れ子にした値を使用してコレクションを作成する場合、入れ子にされた値リストの各要素は、要素型と一致する `Add` メソッドに引数として渡されます。  例として、<xref:System.Collections.Generic.Dictionary%602> を作成し、このキーを `Integer` 型にし、値を `String` 型にするコードを次に示します。  入れ子にされた値リストの各値は、`Dictionary` の <xref:System.Collections.Generic.Dictionary%602.Add%2A> メソッドに照合されます。  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_6.vb)]  
  
 上のコード例は、次のコードと同じ結果になります。  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_7.vb)]  
  
 入れ子にされた値リストは、入れ子の最初のレベルからのみコレクション型の `Add` メソッドに送られます。  入れ子の最初のレベルより下のレベルは、配列リテラルとして扱われ、入れ子にされた値リストはコレクションの `Add` メソッドに照合されません。  
  
## 関連トピック  
  
|||  
|-|-|  
|Title|Description|  
|[How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|コレクション初期化子からの値を使用してコレクションを作成するために使用できる `Add` という拡張メソッドを作成する方法を示します。|  
|[How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|このコレクション クラスに `Add` のメソッドを含めることによってコレクション初期化子を使用する方法を実装 `IEnumerable` 示します。|  
  
## 参照  
 [コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Auto\-Implemented Properties](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)