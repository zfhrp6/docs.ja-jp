---
title: "Scope in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "module scope"
  - "scope, levels"
  - "module level"
  - "procedures, scope"
  - "declared elements, scope"
  - "namespaces, scope"
  - "scope, declared elements"
  - "scope, about scope"
  - "levels of scope"
  - "block scope"
  - "scope, Visual Basic"
  - "procedure scope"
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Scope in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

宣言された要素の*スコープ*とは、名前に修飾子を付けたり [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を使用して有効にすることなく、その要素を参照できるコードの範囲です。  要素は、次のいずれかのレベルのスコープを持つことができます。  
  
|\[レベル\]|Description|  
|-------------|-----------------|  
|ブロック スコープ|要素が宣言されたコード ブロック内でのみ使用可能|  
|プロシージャ スコープ|要素が宣言されたプロシージャ内のすべてのコードで使用可能|  
|モジュール スコープ|要素が宣言されたモジュール内、クラス内、または構造体内のすべてのコードで使用可能|  
|名前空間スコープ|要素が宣言された名前空間内のすべてのコードで使用可能|  
  
 上に列挙したスコープのレベルは、下にいくほどスコープが広くなります。つまり、ブロック スコープが最も狭いスコープ、名前空間スコープが最も広いスコープです。ここでいう*最も狭いスコープ*とは、修飾子を付けずにその要素を参照できるコード範囲が最も小さいという意味です。  詳細については、このページの「スコープのレベル」を参照してください。  
  
## スコープの指定と変数の定義  
 要素のスコープは、要素を宣言するときに指定します。  スコープは以下の要因によって決まります。  
  
-   要素を宣言する領域 \(ブロック、プロシージャ、モジュール、クラス、または構造体\)  
  
-   要素の宣言を含む名前空間  
  
-   要素に宣言するアクセス レベル  
  
 名前が同じでスコープが異なる変数を定義する場合は、予想外の結果を招く可能性があるので注意してください。  詳細については、「[References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。  
  
## スコープのレベル  
 プログラミング要素は、宣言した領域全体にわたって使用できます。  同じ領域内のコードで要素を参照する場合は、名前に修飾子を付ける必要はありません。  
  
### ブロック スコープ  
 ブロックとは、次のように、開始宣言ステートメントと終了宣言ステートメントで囲まれた一連のステートメントです。  
  
-   `Do` と `Loop`  
  
-   `For` `Each` と `Next`  
  
-   `If` と `End If`  
  
-   `Select` と `End Select`  
  
-   `SyncLock` と `End SyncLock`  
  
-   `Try` と `End Try`  
  
-   `While` と `End While`  
  
-   `With` と `End With`  
  
 ブロック内で変数を宣言した場合、その変数はそのブロック内でのみ使用できます。  たとえば、次の例で整数型の変数 `cube` のスコープは `If` と `End If` の間のブロックであるため、実行ステップがこのブロックの外に出てしまうと `cube` を参照できなくなります。  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  スコープがブロック内に制限されている変数でも、有効期間はプロシージャ全体の有効期間と同じです。  プロシージャ内で同じブロックが複数回実行される場合、各ブロック変数には前に実行されたときの値が保持されています。  そのような場合に予想外の結果が生じるのを避けるために、ブロックの先頭ではブロック変数を初期化することをお勧めします。  
  
### プロシージャ スコープ  
 プロシージャ内で宣言した要素は、そのプロシージャの外では使用できません。  要素を使用できるのは、その要素の宣言を含むプロシージャだけです。  このレベルの変数は、*ローカル変数*とも呼ばれます。  ローカル要素を宣言するには、[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を使用します。[Static](../../../../visual-basic/language-reference/modifiers/static.md) キーワードは指定することも省くこともできます。  
  
 プロシージャとブロック スコープの間には密接な関係があります。  プロシージャ内のどのブロックにも含まれていない場所で変数を宣言した場合、その変数は、プロシージャ全体から成るブロックのブロック スコープを持つと見なすことができます。  
  
> [!NOTE]
>  `Static` 変数を含め、すべてのローカル要素は、宣言されたプロシージャ内にプライベートです。  プロシージャ内で [Public](../../../../visual-basic/language-reference/modifiers/public.md) キーワードを使って要素を宣言することはできません。  
  
### モジュール スコープ  
 便宜上、モジュール、クラス、および構造体に対して、*モジュール レベル* という 1 つの用語を使用します。  要素をモジュール レベルで宣言するには、モジュール、クラス、または構造体の中で、プロシージャやブロックの外に宣言ステートメントを配置します。  
  
 モジュール レベルで要素を宣言するときは、選択するアクセス レベルによってスコープが決まります。  また、モジュール、クラス、または構造体を含む名前空間もスコープに影響します。  
  
 [Private](../../../../visual-basic/language-reference/modifiers/private.md) のアクセス レベルを宣言した要素は、モジュール内のすべてのプロシージャから参照できますが、他のモジュール内のコードからは参照できません。  アクセス レベル キーワードを使用しないと、モジュール レベルの `Dim` ステートメントは既定で `Private` になります。  ただし、`Dim` ステートメントで `Private` キーワードを使用すると、スコープとアクセス レベルがより明確になります。  
  
 次の例の場合、モジュール内で定義されているすべてのプロシージャから、文字列変数 `strMsg` を参照できます。  2 番目のプロシージャが呼び出されると、文字列変数 `strMsg` の内容がダイアログ ボックスに表示されます。  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### 名前空間スコープ  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) キーワードまたは [Public](../../../../visual-basic/language-reference/modifiers/public.md) キーワードを使ってモジュール レベルで要素を宣言すると、宣言した名前空間内のすべてのプロシージャで使用できるようになります。  上の例を次のように変更すると、宣言した名前空間内のすべてのコードで文字列変数 `strMsg` を参照できるようになります。  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 名前空間スコープには、入れ子にした名前空間も含まれます。  名前空間内で使用できる要素は、その名前空間内に入れ子にした名前空間の中からも使用できます。  
  
 プロジェクト内に [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)が 1 つもない場合は、プロジェクト全体が同じ名前空間に属します。  この場合、名前空間スコープはプロジェクト スコープであると考えることができます。  モジュール、クラス、または構造体の中の `Public` 要素は、そのプロジェクトを参照するどのプロジェクトからも使用できます。  
  
## スコープの選択  
 変数を宣言する際は、次の点を念頭に置いてスコープを選択する必要があります。  
  
### ローカル変数の利点  
 ローカル変数は、次の理由により、各種の一時的な計算を行う場合に最適です。  
  
-   **名前の競合の回避。**ローカル変数には名前の重複が発生しません。  たとえば、`intTemp` という名前の変数を持つプロシージャを複数作成できます。  それぞれの `intTemp` をローカル変数として宣言する限り、各プロシージャは自分の `intTemp` 以外は認識しません。  いずれかのプロシージャがローカルの `intTemp` の値を変更しても、他のプロシージャの `intTemp` に影響が及ぶことはありません。  
  
-   **メモリの使用量。**ローカル変数は、そのプロシージャの実行中にしかメモリを消費しません。  制御がプロシージャから呼び出し側のコードに戻ると、メモリは解放されます。  逆に、[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) 変数および [Static](../../../../visual-basic/language-reference/modifiers/static.md) 変数は、アプリケーションが実行を終えるまでメモリ リソースを消費するため、これらの変数は必要な場合にのみ使用してください。  *インスタンス変数*は、インスタンスが存在している間メモリを消費します。このため、ローカル変数ほど効率的ではありませんが、`Shared` および `Static` 変数よりも効率的である可能性があります。  
  
### スコープをできるだけ狭くする  
 変数や定数を宣言する場合に、通常、できる限りスコープを狭くすることをお勧めします \(最も狭いのはブロック スコープです\)。  スコープを狭くすると、メモリを節約できます。また、間違った変数を参照する可能性も低くなります。  同様に、プロシージャの呼び出し間で値を保持する必要がある場合だけ、変数を [Static](../../../../visual-basic/language-reference/modifiers/static.md) として宣言してください。  
  
## 参照  
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [How to: Control the Scope of a Variable](../Topic/How%20to:%20Control%20the%20Scope%20of%20a%20Variable%20\(Visual%20Basic\).md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)