---
title: "Delegate Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Delegate"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "delegate keyword"
  - "Delegate statement"
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Delegate Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

デリゲートを宣言します。  デリゲートとは、型の `Shared` メソッド、またはオブジェクトのインスタンス メソッドを参照する参照型です。  パラメーターの型と戻り値の型が一致するプロシージャを使って、このデリゲート クラスのインスタンスを作成できます。  デリゲート インスタンスの作成後は、そのインスタンスを経由してプロシージャを起動できます。  
  
## 構文  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`attrlist`|省略可能です。  このデリゲートに適用される属性の一覧を指定します。  複数の属性を指定するときは、コンマ \(,\) で区切ります。  [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) は、山かっこ \(`<` および `>`\) で囲む必要があります。|  
|`accessmodifier`|省略可能です。  どのようなコードからデリゲートにアクセスできるのかを指定します。  次のいずれかになります。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md) デリゲートを宣言した要素にアクセスできるすべてのコードがアクセスできます。<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md) デリゲートのクラス内のコード、または派生クラスのみがアクセスできます。<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md) デリゲートと同じアセンブリ内のコードだけがアクセスできます。<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md) デリゲートを宣言した要素内のコードだけがアクセスできます。<br /><br /> `Protected Friend` と指定すると、デリゲートのクラス、その派生クラス、または同じアセンブリ内のコードからのみアクセスできます。|  
|`Shadows`|省略可能です。  このデリゲートが、基本クラスにある、同じ名前を持つプログラミング要素、またはオーバーロードされる要素を宣言し直すことを示します。  宣言された要素は、他の任意の種類の要素でシャドウできます。<br /><br /> シャドウされた要素は、その要素をシャドウする派生クラスからは使用できません。ただし、シャドウする要素がアクセスできない要素の場合は例外です。  たとえば、`Private` 要素が基本クラスの要素をシャドウした場合、その `Private` 要素へのアクセス許可を持たないコードは、基本クラスの要素へ代わりにアクセスします。|  
|`Sub`|省略できます。ただし、`Sub` か `Function` のどちらかを指定する必要があります。  指定するプロシージャが、値を返さないデリゲートの `Sub` プロシージャとして宣言されることを示します。|  
|`Function`|省略できます。ただし、`Sub` か `Function` のどちらかを指定する必要があります。  指定するプロシージャが、値を返すデリゲートの `Function` プロシージャとして宣言されることを示します。|  
|`name`|必ず指定します。  デリゲート型の名前を指定します。デリゲート型の標準的な名前付け規則に従って名前を付けます。|  
|`typeparamlist`|省略可能です。  このデリゲートの型パラメーターを一覧表示します。  複数の型パラメーターがある場合は、コンマ \(,\) で区切られます。  必要に応じて、ジェネリックの `In` 修飾子や `Out` 修飾子を使用して、それぞれの型パラメーターをバリアントとして宣言できます。  [Type List](../../../visual-basic/language-reference/statements/type-list.md) はかっこで囲み、冒頭に `Of` キーワードを付けます。|  
|`parameterlist`|省略可能です。  プロシージャが呼び出されたときに渡されるパラメーターのリストです。  [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) はかっこで囲む必要があります。|  
|`type`|`Function` プロシージャを指定する場合は、必ず指定します。  戻り値のデータ型を指定します。|  
  
## 解説  
 `Delegate` ステートメントでは、デリゲート クラスのパラメーターの型と戻り値の型を定義します。  パラメーターの型と戻り値の型が一致するプロシージャを使って、このデリゲート クラスのインスタンスを作成できます。  デリゲート インスタンスの作成後は、デリゲートの `Invoke` メソッドを呼び出すことで、そのインスタンスを経由してプロシージャを起動できます。  
  
 デリゲートは、名前空間、モジュール、クラス、構造体レベルで宣言できますが、プロシージャ内では宣言できません。  
  
 各デリゲート クラスでは、オブジェクト メソッドの仕様を渡すコンストラクターを定義します。  デリゲート コンストラクターに渡す引数は、メソッドへの参照、またはラムダ式である必要があります。  
  
 メソッドへの参照を指定するには、次の構文を使用します。  
  
 `AddressOf` \[`expression`.\]`methodname`  
  
 コンパイル時の `expression` の型は、シグネチャがデリゲート クラスのシグネチャと同じで、指定された名前のメソッドを持つクラスまたはインターフェイスである必要があります。  `methodname` は、共有メソッドまたはインスタンス メソッドのいずれかにできます。  クラスの既定メソッドに対してデリゲートを作成する場合も、`methodname` は省略できません。  
  
 ラムダ式を指定するには、次の構文を使用します。  
  
 `Function` \(\[`parm` As `type`, `parm2` As `type2`, ...\]\) `expression`  
  
 関数のシグネチャは、デリゲート型のシグネチャと一致している必要があります。  ラムダ式の詳細については、「[Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。  
  
 デリゲートの詳細については、「[Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)」を参照してください。  
  
## 使用例  
 次の例では、`Delegate` ステートメントを使って、2 つの数字を操作して数字を返すデリゲートを宣言します。  `DelegateTest` メソッドはこのデリゲートの型のインスタンスを受け取り、デリゲートを使って 1 組の数字を操作します。  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/delegate-statement_1.vb)]  
  
## 参照  
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [共変性と反変性](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)