---
title: "Type List (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StructureConstraint"
  - "vb.StructureConstraint"
  - "ClassConstraint"
  - "vb.ClassConstraint"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "class constraint"
  - "constraints, Visual Basic generic types"
  - "generic parameters"
  - "generics [Visual Basic], constraints"
  - "generics [Visual Basic], type list"
  - "structure constraint"
  - "constraints, in type parameters"
  - "generics [Visual Basic], generic types"
  - "parameters, type"
  - "constraints, Structure keyword"
  - "type parameters, constraints"
  - "types [Visual Basic], generic"
  - "parameters, generic"
  - "generics [Visual Basic], type parameters"
  - "type parameters"
  - "constraints, Class keyword"
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type List (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

*ジェネリック*なプログラミング要素に*型パラメーター*を指定します。  複数のパラメーターを指定するときは、コンマ \(,\) で区切ります。  型パラメーターを 1 つ定義する場合の構文は次のとおりです。  
  
## 構文  
  
```  
  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`genericmodifier`|省略可能です。  ジェネリックなインターフェイスおよびデリゲートでのみ使用できます。  [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) キーワードを使用して共変の型を宣言するか、[In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) キーワードを使用して反変の型を宣言することができます。  「[共変性と反変性](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。|  
|`typename`|必ず指定します。  型パラメーターの名前です。  これはプレースホルダーです。対応する型引数で指定される定義済みの型に置き換えられます。|  
|`constraintlist`|省略可能です。  `typename` に指定可能なデータ型を制約する要件のリストです。  制約を複数指定する場合は、中かっこ \(`{ }`\) で囲み、コンマで区切って記述します。  制約リストには [As](../../../visual-basic/language-reference/statements/as-clause.md) キーワードを付ける必要があります。  `As` はリストの先頭に一度だけ記述します。|  
  
## 解説  
 すべてのジェネリックなプログラミング要素は、型パラメーターを少なくとも 1 つ受け取る必要があります。  型パラメーターは特定の型 \(*構成される要素*\) のプレースホルダーであり、クライアント コードでジェネリック型のインスタンスを作成するときに指定されます。  クラス、構造体、インターフェイス、プロシージャ、またはデリゲートをジェネリックで定義できます。  
  
 ジェネリック型を定義する状況については、「[Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)」を参照してください。  型パラメーターの名前については、「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
## 規則  
  
-   **かっこ。**型パラメーターのリストを指定する場合は、リストをかっこで囲み、[Of](../../../visual-basic/language-reference/statements/of-clause.md) キーワードを使って特定する必要があります。  `Of` はリストの先頭に一度だけ記述します。  
  
-   **制約。**型パラメーターに対する*制約*のリストには、次の項目を任意の組み合わせで定義できます。  
  
    -   任意の数のインターフェイス。  指定する型は、このリストにあるすべてのインターフェイスを実装している必要があります。  
  
    -   1 つ以下のクラス。  指定する型は、そのクラスから継承している必要があります。  
  
    -   `New` キーワード。  指定する型は、ジェネリック型からアクセス可能な、パラメーターを持たないコンストラクターを公開している必要があります。  これは、型パラメーターを 1 つ以上のインターフェイスで制約している場合に使用します。  インターフェイスを実装する型が、必ずしもコンストラクターを公開しているとは限りません。また、コンストラクターのアクセス レベルによっては、ジェネリック型の内部のコードからアクセスできない可能性もあります。  
  
    -   `Class` キーワードまたは `Structure` キーワード。  `Class` キーワードでは、ジェネリック型パラメーターに渡すすべての型引数を必ず参照型 \(文字列、配列、デリゲート、クラスから作成されたオブジェクトなど\) にする制約を指定できます。  `Structure` キーワードでは、ジェネリック型パラメーターに渡すすべての型引数を必ず値型 \(構造体、列挙体、基本データ型など\) にする制約を指定できます。  同じ `constraintlist` で `Class` と `Structure` の両方を指定することはできません。  
  
     指定する型は、`constraintlist` に定義されたすべての要件を満たす必要があります。  
  
     型パラメーターの制約は、それぞれ他の型パラメーターの制約と関連しません。  
  
## \[動作\]  
  
-   **コンパイル時の代入。**ジェネリックなプログラミング要素から構築型を作成する場合は、各型パラメーターに対して定義済みの型を指定します。  Visual Basic コンパイラは、ジェネリックな要素の内部に出現するすべての `typename` に、指定された型を代入します。  
  
-   **制約の省略。**型パラメーターに制約を指定しなければ、コードはその型パラメーターにおいて[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) でサポートされた操作およびメンバーに制限されます。  
  
## 使用例  
 ジェネリックなディクショナリ クラスのスケルトン定義の例を次に示します。スケルトン関数がディクショナリに新しいエントリを追加しています。  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/type-list_1.vb)]  
  
## 使用例  
 `dictionary` がジェネリックなので、コードはそこからさまざまなオブジェクトを作成できます。各オブジェクトは同じ関数を含みますが、さまざまなデータ型に対して処理を実行します。  文字列 \(`String`\) のエントリと整数 \(`Integer`\) のキーを使って `dictionary` オブジェクトを作成するコード行の例を次に示します。  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/type-list_2.vb)]  
  
## 使用例  
 先の例と同等のスケルトン定義の例は、次のとおりです。  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/type-list_3.vb)]  
  
## 参照  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [New Operator](../../../visual-basic/language-reference/operators/new-operator.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [共変性と反変性](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)