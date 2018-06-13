---
title: 構造体とクラス (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: e64b54b93463845dd9afd0c0efd0e39f20cab1ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654123"
---
# <a name="structures-and-classes-visual-basic"></a>構造体とクラス (Visual Basic)
Visual Basic では、構造体とクラスは、両方のエンティティに同じ機能のほとんどがサポートされる結果の構文を統一します。 ただし、構造体とクラスの重要な違いもできます。  
  
 クラスが参照型になるというメリットがある、参照を渡すことが、そのすべてのデータと構造体変数を渡すより効率的です。 その一方で、構造体には、グローバル ヒープにメモリの割り当ては不要です。  
  
 構造体から継承することはできませんので構造体を拡張する必要がないオブジェクトに対してのみ使用してください。 構造体を使用すると、オブジェクトを作成する小さいインスタンス サイズの場合は、構造体とクラスのパフォーマンス特性を考慮します。  
  
## <a name="similarities"></a>類似点  
 構造体とクラスは、次の点で似ています。  
  
-   これらはいずれも*コンテナー*型、メンバーとして他の型が含まれていることを意味します。  
  
-   両方があるメンバーで、コンス トラクター、メソッド、プロパティ、フィールド、定数、列挙型、イベント、およびイベント ハンドラーに含めることができます。 ただし、これらのメンバーの宣言とを混同しないでください*要素*構造体の。  
  
-   両方のメンバーも、個別のアクセス レベル。 たとえば、1 つのメンバーを宣言できます`Public`別および`Private`です。  
  
-   インターフェイスを実装両方できます。  
  
-   両方が共有できますコンス トラクター、またはパラメーターなし。  
  
-   両方を公開できます、*既定プロパティ*プロパティは、少なくとも 1 つのパラメーターを受け取りますが、します。  
  
-   両方を宣言でき、イベントを発生させるし、デリゲートを宣言できます。  
  
## <a name="differences"></a>相違点  
 構造体とクラスは、次のとおりで異なります。  
  
-   構造体は*値の型*; クラスは、*型参照*です。 クラス型としてのデータへの参照を含むのではなく、構造体の型の変数には、構造体のデータが含まれています。  
  
-   使用して構造はスタック割り当てです。クラスは、ヒープの割り当てを使用します。  
  
-   構造体のすべての要素は`Public`クラス変数の既定では、定数は、`Private`既定では、他のクラス メンバーは`Public`既定です。 クラスのメンバーには、この動作は、既定の Visual Basic 6.0 のシステムとの互換性を提供します。  
  
-   構造体の有効期限がありますには、少なくとも 1 つの非共有変数または非共有、カスタム イベントの要素です。クラスは、完全に空にすることができます。  
  
-   構造体の要素として宣言することはできません`Protected`; クラスのメンバーのことができます。  
  
-   構造体のプロシージャはイベントを処理できる場合にのみ、[共有](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub`プロシージャ、およびだけでは、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 任意のクラスのプロシージャは、いずれかのを使用して、イベントを処理できます[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)キーワードまたは`AddHandler`ステートメントです。 詳細については、「[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)」を参照してください。  
  
-   構造体の変数宣言には、初期化子または配列の初期サイズを指定できません。クラスの変数宣言できます。  
  
-   構造体を暗黙的に継承、<xref:System.ValueType?displayProperty=nameWithType>クラスし、その他の型から継承できませんクラスが以外の任意のクラスまたはクラスから継承できます<xref:System.ValueType?displayProperty=nameWithType>です。  
  
-   構造体が継承可能な; できません。クラスがあります。  
  
-   構造体は決して終了しているため、共通言語ランタイム (CLR) を呼び出すことはありません、<xref:System.Object.Finalize%2A>メソッドすべての構造をクラスが、ガベージ コレクター (GC) を呼び出すによって終了<xref:System.Object.Finalize%2A>アクティブな参照がないを検出した場合にクラス残りの。  
  
-   構造体には、コンス トラクターは不要します。クラスでは。  
  
-   構造体を持つことができますパラメーターを取る場合にのみ、非共有コンス トラクター。パラメーターの有無は、クラスでそれらを持つことができます。  
  
 すべての構造体には、パラメーターなし暗黙的なパブリック コンス トラクターがあります。 このコンス トラクターでは、構造体のすべてのデータ要素が既定値に初期化します。 この動作を再定義することはできません。  
  
## <a name="instances-and-variables"></a>インスタンスと変数  
 構造体は値型であるために、各構造体変数は永続的に個別の構造体のインスタンスにバインドします。 クラスは参照型、オブジェクト変数は、異なる時刻でさまざまなクラスのインスタンスを参照できます。 この違いでは、次の方法で構造体とクラスの使用に影響します。  
  
-   **初期化します。** 構造体変数には、構造体のパラメーターなしのコンス トラクターを使用して要素の初期化で、暗黙的に含まれています。 したがって、`Dim s As struct1`は等価`Dim s As struct1 = New struct1()`です。  
  
-   **変数を代入しています。** 間、1 つの構造体変数を割り当てるか、プロシージャの引数に構造体のインスタンスを渡すときに、変数のすべての要素の現在の値は、新しい構造にコピーされます。 間、1 つのオブジェクト変数を割り当てるか、プロシージャをオブジェクト変数を渡すときに参照ポインターだけがコピーされます。  
  
-   **何を割り当てます。** 値を割り当てることができます[Nothing](../../../../visual-basic/language-reference/nothing.md)構造体を変数が、インスタンスは引き続き、変数に関連付けられています。 そのメソッドを呼び出すして変数の要素が、割り当てで再初期化されますが、そのデータ要素にアクセスします。  
  
     オブジェクト変数を設定する場合とは異なり、 `Nothing`、すべてのクラスのインスタンスから関連付けを解除し、別のインスタンスを割り当てるまで、変数をメンバーにアクセスすることはできません。  
  
-   **複数のインスタンス。** オブジェクト変数が異なるタイミングでそれに割り当てられている別のクラスのインスタンスを持つことができ、いくつかのオブジェクト変数が、同時に、同じクラスのインスタンスを参照できます。 クラス メンバーの値に加えた変更は、同じインスタンスを指す別の変数を使用してアクセスするときにそのメンバーに影響します。  
  
     ただし、構造体の要素は、独自のインスタンス内で分離されます。 他のインスタンスが同じであっても、別の構造体変数にその値への変更は反映されません`Structure`宣言します。  
  
-   **等しいかどうか。** 2 つの構造の等価テストは、要素でテストを実行する必要があります。 使用して 2 つのオブジェクト変数を比較することができます、<xref:System.Object.Equals%2A>メソッドです。 <xref:System.Object.Equals%2A> 2 つの変数が同じインスタンスをポイントするかどうかを示します。  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [構造体とその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
