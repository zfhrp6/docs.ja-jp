---
title: "Namespace Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Namespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "namespaces, root"
  - "Namespace statement"
  - "namespaces, nested"
  - "declaring namespaces, syntax"
  - "namespaces, declaring"
  - "root namespaces"
  - "declarations, namespaces"
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: 39
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 39
---
# Namespace Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

名前空間の名前を宣言し、後続のソース コードがその名前空間内にコンパイルされるようにします。  
  
## 構文  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## 指定項目  
 グローバル  
 省略可能です。  プロジェクトのルート名前空間の名前空間を定義する。  「[Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)」を参照してください。  
  
 `name`  
 必ず指定します。  名前空間を識別する一意の前を指定します。  有効な Visual Basic 識別子を指定する必要があります。  詳細については、「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
 `componenttypes`  
 省略可能です。  名前空間を構成する要素を指定します。  これらはに含まれていますが列挙型構造体モジュールインターフェイスクラスデリゲート他の名前空間はありません。  
  
 `End Namespace`  
 `Namespace` ブロックを終了します。  
  
## 解説  
 名前空間は、コードを組織化する枠組みとして使用されます。  他のプログラムやアプリケーションに公開されるプログラミング要素を分類および表現する手段となります。  名前空間のデータ型を持つように名前空間を  *型*  という意味でクラスではプログラミング要素を宣言できない構成しないことに注意してください。  
  
 `Namespace` ステートメントの後に宣言したすべてのプログラミング要素は、その名前空間に属します。  最後に宣言された名前空間の中に要素をコンパイルする処理は、`End Namespace` ステートメントまたは別の `Namespace` ステートメントが現れるまで続けられます。  
  
 名前空間が既に定義されている場合、プロジェクトの外部にある名前空間でも、プログラミング要素をそこに追加できます。  これを行うにはその名前空間に要素をコンパイルするように Visual Basic に指示するために `Namespace` のステートメントを使用します。  
  
 `Namespace` ステートメントは、ファイル レベルまたは名前空間レベルでのみ使用できます。  つまり、名前空間の*宣言コンテキスト*は、ソース ファイルまたは別の名前空間のどちらかである必要があり、クラス、構造体、モジュール、インターフェイス、またはプロシージャでは宣言できません。  詳細については、「[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 名前空間は、別の名前空間の内部に宣言できます。  宣言できる入れ子のレベルに厳密な制限はありませんが、最深部の名前空間に宣言した要素に他のコードからアクセスする場合、入れ子の階層にあるすべての名前空間を含む修飾文字列を使用する必要があることに注意してください。  
  
## アクセス レベル  
 名前空間は `Public` のアクセス レベルを持つようにします。  名前空間には、同じプロジェクト内のコード、プロジェクトを参照する他のプロジェクト、およびプロジェクトからビルドされたアセンブリからアクセスできます。  
  
 名前空間レベルで宣言したプログラミング要素、つまり他の要素の内部ではなく名前空間の内部で宣言したプログラミング要素は、アクセス レベルが `Public` または `Friend` になります。  このような要素のアクセス レベルは、特に指定しなければ、既定の `Friend` になります。  名前空間レベルで宣言できる要素は、クラス、構造体、モジュール、インターフェイス、列挙、およびデリゲートです。  詳細については、「[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
## ルート名前空間  
 プロジェクト内のすべての名前空間の名前は、*ルート名前空間*に基づきます。  Visual Studio では、プロジェクト名がプロジェクト内のすべてのコードの既定のルート名前空間として割り当てられます。  たとえば、プロジェクト名が `Payroll` である場合、そのプログラミング要素は `Payroll` 名前空間に属します。  `Namespace funding` と宣言した場合、この名前空間の完全名は `Payroll.funding` になります。  
  
 前のジェネリックなリスト クラスの例のように、既存の名前空間を `Namespace` ステートメントで指定する場合は、ルート名前空間を null 値に設定できます。  この設定を行うには、**\[プロジェクト\]** メニューの **\[プロジェクトのプロパティ\]** をクリックし、**\[ルート名前空間\]** ボックスをクリアして空にします。  この設定を前記のジェネリックなリスト クラスの例で行わなかった場合、Visual Basic コンパイラは `System.Collections.Generic` を `Payroll` プロジェクト内の `Payroll.System.Collections.Generic` という完全名を持つ新しい名前空間と見なします。  
  
 `Global` キーワードを使って、プロジェクトの外部で定義された名前空間の要素を参照することもできます。  この方法を使うと、プロジェクト名をルート名前空間として使い続けることができます。  それにより、意に反してプログラミング要素が既存の名前空間の要素と共にマージされる可能性は少なくなります。  詳細については「 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) の完全修飾名に Global キーワード」を参照してください。  
  
 `Global` のキーワードは名前空間をステートメントで使用できます。  これはプロジェクトのルート名前空間の名前空間を定義することができます。  詳細については「 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) の名前空間のステートメント Global キーワード」を参照してください。  
  
 **修復。**ルート名前空間が、予期しない名前空間の連結を招く場合があります。  プロジェクトの外部で定義された名前空間への参照を作成すると、Visual Basic コンパイラは、その名前空間をルート名前空間内の入れ子の名前空間として解釈します。  その場合、コンパイラでは、外部の名前空間で定義されたデータ型を認識しません。  これを回避するには「ルート名前空間 " に説明されているようにnull 値はルート名前空間」に設定するか外部名前空間の要素にアクセスするに `Global` のキーワードを使用します。  
  
## 属性と修飾子  
 名前空間には属性を適用できません。  属性は、アセンブリのメタデータに情報を提供します。この情報は、名前空間のようなソース分類子にとって意味を持ちません。  
  
 名前空間には、アクセス修飾子またはプロシージャ修飾子、またはその他の修飾子を適用できません。  型ではないので、このような修飾子は意味を持ちません。  
  
## 使用例  
 次のコード例は、入れ子の関係になるように 2 つの名前空間を宣言します。  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## 使用例  
 入れ子になった複数の名前空間を 1 行で宣言するコード例を次に示します。これは前のコード例と同じ意味を持ちます。  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## 使用例  
 次のコード例は、前の例で定義したクラスにアクセスします。  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## 使用例  
 次のコード例は、新しいジェネリックなリスト クラスのスケルトンを定義し、それを <xref:System.Collections.Generic?displayProperty=fullName> 名前空間に追加します。  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## 参照  
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)