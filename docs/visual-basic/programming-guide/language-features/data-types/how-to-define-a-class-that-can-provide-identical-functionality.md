---
title: "方法: 複数のデータ型に同一の機能を提供できるクラスを定義する (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "データ型引数、使用"
  - "型パラメーター、定義"
  - "データ型引数、定義"
  - "引数 [Visual Basic]、データ型"
  - "Of キーワード、使用"
  - "制約、Visual Basic ジェネリック型"
  - "ジェネリック パラメーター"
  - "データ型パラメーター"
  - "データ型パラメーター、使用"
  - "ジェネリック [Visual Basic]、型パラメーターを持つクラスを定義"
  - "データ型 [Visual Basic]、パラメーターとしての"
  - "データ型 [Visual Basic]、引数としての"
  - "パラメーター、型"
  - "型引数"
  - "型 [Visual Basic]、ジェネリック"
  - "パラメーター、ジェネリック"
  - "型パラメーター"
  - "データ型引数"
  - "パラメーター、データ型"
  - "ジェネリック [Visual Basic]、ジェネリック型の定義"
  - "データ型パラメーター、定義"
  - "型引数、定義"
  - "引数 [Visual Basic]、型"
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# 方法: 複数のデータ型に同一の機能を提供できるクラスを定義する (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

複数の異なるデータ型に同一の機能を提供するオブジェクトを作成するために使用できるクラスを定義できます。 これを行うには、1 つ以上の*型パラメーター*を定義内で指定します。 このようなクラスは、さまざまなデータ型を使用するオブジェクトのテンプレートとして使用できます。 この方法で定義したクラスは、*ジェネリック クラス*と呼ばれます。  
  
 ジェネリック クラスを定義する利点は、クラスを一度だけ定義すれば、コードの中でそれを使って、さまざまなデータ型を使用する多くのオブジェクトを作成できることです。 これにより、クラスを `Object` 型で定義した場合よりパフォーマンスが向上します。  
  
 クラスに加えて、ジェネリックの構造体、インターフェイス、プロシージャ、デリゲートを定義して利用することもできます。  
  
### 型パラメーターを持つクラスを定義するには  
  
1.  通常の方法でクラスを定義します。  
  
2.  クラス名の直後に `(Of` *typeparameter*`)` を追加し、型パラメーターを指定します。  
  
3.  複数の型パラメーターがある場合は、かっこ内にコンマ区切りのリストを指定します。`Of` キーワードは繰り返さないでください。  
  
4.  型パラメーターに対して単純な代入以外の操作を実行する場合は、その型パラメーターの後に `As` 句を付けて 1 つ以上の*制約*を追加します。 制約は、その型パラメーターに渡される型が、たとえば以下のような要件を満たすことを保証します。  
  
    -   コードで実行する `>` などの演算をサポートする  
  
    -   コードでアクセスするメソッドなどのメンバーをサポートする  
  
    -   パラメーターなしのコンストラクターを公開する  
  
     制約を指定しない場合、コードで使用できる演算とメンバーは、[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) でサポートされるものだけになります。 詳細については、「[Type List](../../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。  
  
5.  渡された型を使って宣言する必要のある各クラス メンバーを識別し、それを `As` `typeparameter` として宣言します。 これは、内部ストレージ、プロシージャのパラメーター、戻り値に適用されます。  
  
6.  コードでは、`itemType` に渡される可能性があるすべてのデータ型でサポートされる演算とメソッドだけを使用します。  
  
     次のコード例は、ごく単純なリストを管理するクラスを定義しています。 このクラスは、リストを内部配列 `items` に格納します。このクラスを使用するコードでは、このリストの要素のデータ型を宣言できます。 パラメーター化されたコンストラクターを使うと、コードで `items` の上限を設定できます。既定のコンストラクターでは、この上限は 9 \(合計で 10 アイテム\) に設定されます。  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     `simpleList` からは、`Integer` 値のリストを格納するクラス、`String` 値のリストを格納するクラス、`Date` 値のリストを格納するクラスなどを宣言できます。 リスト メンバーのデータ型が異なるだけで、これらすべてのクラスから作成されるオブジェクトの動作はまったく同じです。  
  
     使用するコードから `itemType` に渡す型引数としては、`Boolean` や `Double` などの組み込みの型、構造体、列挙、任意の型のクラス \(アプリケーションで独自に定義したクラスを含む\) を使用できます。  
  
     `simpleList` クラスをテストするには、次のコードを使用します。  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)   
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)   
 [方法 : ジェネリック クラスを使用する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)