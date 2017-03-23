---
title: "構造体とクラス (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures
- classes [Visual Basic]
- structures, compared to classes
- structures, structure variables
- structure variables
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e7402ec0fcfc279470d39a4919d3b5ec8b5d9dff
ms.lasthandoff: 03/13/2017

---
# <a name="structures-and-classes-visual-basic"></a>構造体とクラス (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]構造体と結果の両方のエンティティに同じ機能のほとんどがサポートされると共に、クラスの構文を統一します。 ただし、構造体とクラスの重要な違いもします。  
  
 クラスの参照型になるというメリットがある、参照を渡すことは、そのすべてのデータと構造体変数を渡すことよりも効率的です。 その一方で、構造体には、グローバル ヒープにメモリの割り当ては不要です。  
  
 構造体から継承することはできませんので構造体を拡張する必要のないオブジェクトに対してのみ使用してください。 作成するオブジェクト s インスタンスのサイズがあり、構造体とクラスのパフォーマンス特性を考慮に入れる場合は、構造体を使用します。  
  
## <a name="similarities"></a>類似点  
 構造体とクラスは、次の点で似ています。  
  
-   どちらも*コンテナー*型、メンバーとして他の種類が含まれていることを意味します。  
  
-   両方があるメンバーで、コンス トラクター、メソッド、プロパティ、フィールド、定数、列挙型、イベント、およびイベント ハンドラーを含めることができます。 ただし、これらのメンバー宣言とを混同しないでください*要素*構造体の。  
  
-   両方のメンバーも、個別のアクセス レベル。 たとえば、1 つのメンバーを宣言できます`Public`別`Private`します。  
  
-   インターフェイスを両方実装できます。  
  
-   両方が共有できますコンス トラクター、パラメーターの有無。  
  
-   両方を公開できます、*既定プロパティ*、そのプロパティは、少なくとも&1; つのパラメーターを受け取ります。  
  
-   両方を宣言してイベントを発生させるし、デリゲートを宣言できます。  
  
## <a name="differences"></a>相違点  
 構造体とクラスは、次のとおりで異なります。  
  
-   構造体は*値の型*; クラスは、*参照型*します。 データとしてクラス型への参照を含むのではなく、構造体型の変数には、構造体のデータが含まれています。  
  
-   スタックの割り当てを使用して構造クラスは、ヒープ割り当てを使用します。  
  
-   すべての構造体要素`Public`既定ではクラスの変数と定数は`Private`既定では、他のクラス メンバーは`Public`既定では。 クラス メンバーの場合は、この動作は、既定の Visual Basic 6.0 システムとの互換性を提供します。  
  
-   構造体の有効期限が必要に少なくとも&1; つの非共有変数または非共有の非カスタム イベントの要素です。クラスは、完全に空にすることができます。  
  
-   構造体の要素として宣言できません`Protected`; クラス メンバーにします。  
  
-   構造体のプロシージャがである場合にのみイベントを処理、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`プロシージャとのことでのみ、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md);、クラスのプロシージャは、いずれかを使用して、イベントを処理できます、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)キーワードまたは`AddHandler`ステートメントです。 詳細については、次を参照してください。[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)です。  
  
-   構造体の変数宣言は、初期化子、または配列の初期サイズを指定できません。クラスの変数宣言ことができます。  
  
-   構造体を暗黙的に継承、<xref:System.ValueType?displayProperty=fullName>クラスし、その他の型から継承できないクラスは、任意のクラスまたは<xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName>以外のクラスから継承できます</xref:System.ValueType?displayProperty=fullName>  
  
-   構造体は、継承可能な; がないです。クラスです。  
  
-   構造体が決して終了して、共通言語ランタイム (CLR) を呼び出すことはありませんので、<xref:System.Object.Finalize%2A>メソッドすべての構造をクラスは、ガベージ コレクター (GC) を呼び出すで終了<xref:System.Object.Finalize%2A>アクティブな参照が残っていないを検出した場合にクラスにします</xref:System.Object.Finalize%2A></xref:System.Object.Finalize%2A>。  
  
-   構造体には、コンス トラクターは不要します。クラスでは。  
  
-   構造体のパラメーターになる場合にのみ、非共有コンス トラクターパラメーターの有無は、クラスでを設定できます。  
  
 すべての構造体には、パラメーターを指定しない暗黙の型のパブリック コンス トラクターがあります。 このコンス トラクターでは、既定値に構造体のすべてのデータ要素を初期化します。 この動作を再定義することはできません。  
  
## <a name="instances-and-variables"></a>インスタンスと変数  
 構造体は値型であるために、各構造体変数は永続的に個別の構造体のインスタンスにバインドします。 クラスは参照型、オブジェクト変数が異なる時間にさまざまなクラスのインスタンスを参照できます。 このような区別では、次の方法で構造体とクラスの使用に影響します。  
  
-   **初期化します。** 構造体変数には、暗黙的に、構造体のパラメーターなしのコンス トラクターを使用して要素の初期化が含まれます。 したがって、`Dim s As struct1`は`Dim s As struct1 = New struct1()`です。  
  
-   **変数の割り当てください。** 1 つの構造体変数を別に代入するか、またはプロシージャの引数に構造体のインスタンスを渡すと、変数のすべての要素の現在の値は、新しい構造にコピーされます。 1 つのオブジェクト変数を別に代入するか、またはオブジェクト変数をプロシージャに渡すと、参照ポインターだけがコピーされます。  
  
-   **Nothing を代入します。** 値を割り当てることができます[Nothing](../../../../visual-basic/language-reference/nothing.md)構造体へのインスタンスでは、変数はまだ復旧して、変数に関連付けられています。 代入によって可変要素が再初期化がそのデータ要素にアクセスしたりメソッドを呼び出したりすることができます。  
  
     これに対して、オブジェクト変数を設定した場合に`Nothing`、任意のクラス インスタンスの関連付けを解除し、別のインスタンスを割り当てるまで、変数を使ってメンバーにアクセスすることはできません。  
  
-   **複数のインスタンス。** オブジェクト変数が、異なる時期に割り当てられた別のクラス インスタンスを持つことができ、複数のオブジェクト変数が、同時に、同じクラスのインスタンスを参照できます。 クラスのメンバーの値に加えた変更は、同じインスタンスを指す別の変数を使用してアクセスするときにそのメンバーに影響します。  
  
     ただし、構造体の要素は、独自のインスタンス内で分離されます。 他の同じインスタンスであっても、別の構造体変数にその値への変更は反映されません`Structure`宣言します。  
  
-   **等しいかどうか。** 2 つの構造の等価テストは、要素でテストを実行する必要があります。 使用して&2; つのオブジェクト変数を比較することができます、<xref:System.Object.Equals%2A>メソッド</xref:System.Object.Equals%2A>。 <xref:System.Object.Equals%2A>2 つの変数が同じインスタンスを参照するかどうかを示します。</xref:System.Object.Equals%2A>  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [構造体およびその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
