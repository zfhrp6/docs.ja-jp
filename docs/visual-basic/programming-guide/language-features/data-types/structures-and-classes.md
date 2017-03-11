---
title: "Structures and Classes (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], vs. structures"
  - "structures"
  - "classes [Visual Basic]"
  - "structures, compared to classes"
  - "structures, structure variables"
  - "structure variables"
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Structures and Classes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、構造体とクラスの構文が統一され、両方のエンティティでほとんど同じ機能がサポートされるようになりました。  ただし、構造体とクラスの間には重要な違いもあります。  
  
 クラスには、参照型としての利点があります。たとえば、参照型を渡す方が、すべてのデータが格納されている構造体変数を渡すよりも効率的です。  一方、構造体の場合は、グローバル ヒープにメモリを割り当てる必要がありません。  
  
 構造体からは継承ができないため、構造体は拡張する必要のないオブジェクトにだけ使用することをお勧めします。  構造体は、作成するオブジェクトのインスタンスのサイズが小さい場合に使用します。その場合はクラスと構造体の特性の違いを考慮してください。  
  
## 類似点  
 構造体とクラスの類似点は次のとおりです。  
  
-   どちらも *container* 型であり、他の型をメンバーとして含みます。  
  
-   どちらにもメンバーが含まれます。メンバーとしては、コンストラクター、メソッド、プロパティ、フィールド、定数、列挙値、イベント、およびイベント ハンドラーを含むことができます。  しかし、これらのメンバーと、宣言された構造体の*要素*とを混同しないでください。  
  
-   どちらのメンバーにも、個別のアクセス レベルを設定できます。  たとえば、一方のメンバーを `Public` と宣言し、他方のメンバーを `Private` と宣言することができます。  
  
-   どちらもインターフェイスを実装できます。  
  
-   どちらもパラメーター付きまたはパラメーターなしの共有コンストラクターを含むことができます。  
  
-   どちらも*既定のプロパティ*を公開できます。ただし、少なくとも 1 つのパラメーターを指定する必要があります。  
  
-   どちらもイベントを宣言し発生させて、デリゲートを宣言できます。  
  
## 異なる点  
 構造体とクラスの違いは次のとおりです。  
  
-   構造体は*値型*、クラスは*参照型*です。  クラス型がデータへの参照を格納するのとは異なり、構造体型の値は構造体のデータそのものを格納します。  
  
-   構造体はスタック割り当てを使用し、クラスはヒープ割り当てを使用します。  
  
-   構造体のすべての要素は既定で `Public` です。クラスでは、変数および定数は既定で `Private`、他のメンバーは既定で `Public` です。  これにより、クラスのメンバーは Visual Basic 6.0 の既定値システムとの互換性を持ちます。  
  
-   構造体には少なくとも 1 つの共有されない変数、または共有されない非カスタムのイベント要素を含む必要がありますが、クラスは完全に空にすることができます。  
  
-   構造体の要素は、`Protected` として宣言できませんが、クラス メンバーは宣言できます。  
  
-   構造体のプロシージャは、[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` プロシージャである場合にだけ、[AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)を使用してのみイベントを処理できますが、クラスのプロシージャはどれでも、[Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) キーワードまたは `AddHandler` ステートメントを使用してイベントを処理できます。  詳細については、「[Events](../../../../visual-basic/programming-guide/language-features/events/events.md)」を参照してください。  
  
-   構造体の変数宣言では、初期化子または配列の初期サイズを指定できませんが、クラスの変数宣言では指定できます。  
  
-   構造体は暗黙に <xref:System.ValueType?displayProperty=fullName> クラスから継承し、それ以外の型からは継承できませんが、クラスは <xref:System.ValueType?displayProperty=fullName> 以外のすべてのクラスから継承できます。  
  
-   構造体は継承できませんが、クラスは継承できます。  
  
-   構造体は終了されないため、共通言語ランタイム \(CLR: Common Language Runtime\) は構造体に対して <xref:System.Object.Finalize%2A> メソッドを呼び出しませんが、クラスはガベージ コレクターによって終了され、ガベージ コレクターはアクティブな参照が残っていないことを検出すると、クラスに対して <xref:System.Object.Finalize%2A> を呼び出します。  
  
-   構造体はコンストラクターを必要としませんが、クラスには必要です。  
  
-   構造体にはパラメーターを取る場合にだけ非共有コンストラクターを含むことができますが、クラスにはパラメーターの有無には関係なく非共有コンストラクターを含むことができます。  
  
 すべての構造体には、パラメーターがない暗黙のパブリック コンストラクターが含まれます。  このコンストラクターによって、構造体のすべてのデータ要素が既定値に初期化されます。  この動作は再定義できません。  
  
## インスタンスと変数  
 構造体は値型であるため、各構造体変数は個別の構造体インスタンスに恒久的に関連付けされます。  一方、クラスは参照型であり、オブジェクト変数はさまざまなクラス インスタンスを異なる時点で参照できます。  この違いは、構造体とクラスの使用方法に次のように影響します。  
  
-   **初期化。**構造体変数には、構造体のパラメーターなしコンストラクターを使って、要素の初期化が暗黙的に含まれます。  したがって、`Dim s As struct1` は `Dim s As struct1 = New struct1()` に相当します。  
  
-   **変数の割り当て。**構造体変数を別の構造体変数に代入するか、または構造体インスタンスをプロシージャ引数に渡すと、すべての変数要素の現在の値が新しい構造体にコピーされます。  オブジェクト変数を別のオブジェクト変数に代入するか、またはオブジェクト変数をプロシージャに渡すと、参照ポインターだけがコピーされます。  
  
-   **Nothing の割り当て。**構造体変数には [Nothing](../../../../visual-basic/language-reference/nothing.md) 値を割り当てることができますが、インスタンスは引き続き変数に関連付けられています。  変数要素は代入によって再初期化されますが、以降もその変数のメソッドを呼び出したり、そのデータ要素にアクセスしたりできます。  
  
     一方、オブジェクト変数を `Nothing` に設定した場合は、クラス インスタンスとの関連付けが解除され、別のインスタンスを代入するまでその変数をとおしてメンバーにアクセスすることはできません。  
  
-   **複数のインスタンス。**オブジェクト変数には異なる時点で異なるクラス インスタンスを代入でき、複数のオブジェクト変数が同時に同じクラス インスタンスを参照できます。  クラスのメンバーの値に加えた変更は、同じインスタンスを指す別の変数をとおしてアクセスされたときにそのメンバーに反映されます。  
  
     一方、構造体の要素は、インスタンスごとに独立しています。  メンバーの値に加えられた変更は、他の構造体変数には反映されません。同じ `Structure` 宣言の他のインスタンスであっても反映されません。  
  
-   **等値式。**2 つの構造体の等価テストは、要素ごとに実行する必要があります。  <xref:System.Object.Equals%2A> メソッドを使用して、2 つのオブジェクト変数を比較できます。  <xref:System.Object.Equals%2A> は、2 つの変数が同じインスタンスを指しているかどうかを示します。  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)