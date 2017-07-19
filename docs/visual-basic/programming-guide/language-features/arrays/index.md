---
title: "Visual Basic における配列 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Array
dev_langs:
- VB
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: e0a5ab6a7b3ee752af6b58a35a11e4fc0fb2b08a
ms.openlocfilehash: cc7f5e28831cfe6ec12526d7dac5b12c208fb05a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/03/2017

---
# <a name="arrays-in-visual-basic"></a>Visual Basic における配列
配列は、学校の各学年の生徒の数など、互いに論理的に関連する一連の値です。  Visual Basic for Applications (VBA) の配列についてのヘルプが必要な場合は、 [言語リファレンス](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx)を参照してください。  
  
 配列を使うと、これらの関連する値を同じ名前で参照できます。配列の各要素を区別するには、インデックスまたは添字と呼ばれる番号を使います。 個々の値は、配列の要素と呼ばれます。 これは、インデックス 0 から最も大きいインデックス値まで連続しています。  
  
 配列とは対照的に、単一の値が含まれている変数は *スカラー* 変数と呼ばれます。  
  
 説明する前に、簡単な例をいくつか紹介します。  
  
```vb  
'Declare a single-dimension array of 5 values  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set array element values  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
'Redefine the size of an existing array retaining the current values  
ReDim Preserve numbers(15)  
  
'Redefine the size of an existing array, resetting the values  
ReDim numbers(15)  
  
'Declare a multi-dimensional array  
Dim matrix(5, 5) As Double  
  
'Declare a multi-dimensional array and set array element values  
Dim matrix = New Integer(4, 4) {{1, 2}, {3, 4}, {5, 6}, {7, 8}}  
  
'Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 **このトピックの内容**  
  
-   [単純な配列の配列要素](#BKMK_ArrayElements)  
  
-   [配列の作成](#BKMK_CreatingAnArray)  
  
-   [配列への値の格納](#BKMK_StoringValues)  
  
-   [配列への初期値の取り込み](#BKMK_Populating)  
  
    -   [入れ子になった配列リテラル](#BKMK_NestedArrayLiterals)  
  
-   [配列の反復処理](#BKMK_Iterating)  
  
-   [戻り値およびパラメーターとしての配列](#BKMK_ReturnValues)  
  
-   [ジャグ配列](#BKMK_JaggedArrays)  
  
-   [長さ 0 の配列](#BKMK_ZeroLength)  
  
-   [配列のサイズ](#BKMK_ArraySize)  
  
-   [配列の型および他の型](#BKMK_ArrayTypes)  
  
-   [配列の代わりとしてのコレクション](#BKMK_Collections)  
  
##  <a name="BKMK_ArrayElements"></a> 単純な配列の配列要素  
 次の例では、学校の各学年の生徒の数を保持するために、配列変数を宣言しています。  
  
 [!code-vb[VbVbalrArrays#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#2)]  
  
 上の例の `students` 配列には、7 つの要素が含まれています。 要素のインデックスの範囲は 0 から 6 までです。 7 つの変数を宣言するよりも、この配列の方が簡単です。  
  
 `students`配列を次の図に示します。 配列の各要素は、次のとおりです。  
  
-   要素のインデックスは、学年を表します (インデックス 0 は幼稚園を表します)。  
  
-   要素に含まれている値は、その学年の生徒の数を表します。  
  
 ![生徒数を示す配列の図](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
"生徒" 配列の要素  
  
 次の例は、 `students`配列の先頭の要素、2 番目の要素、および最後の要素を参照する方法を示します。  
  
 [!code-vb[VbVbalrArrays#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#3)]  
  
 インデックスを持たない配列変数名だけを使用して、配列全体を参照できます。  
  
 前の例の `students` 配列では、1 つのインデックスが使用されており、これを 1 次元と言います。 複数のインデックスまたは添字が使用されている配列は、多次元と呼ばれます。 詳細については、このトピックの残りの部分と「 [Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)」を参照してください。  
  
##  <a name="BKMK_CreatingAnArray"></a> 配列の作成  
 配列のサイズは、さまざまな方法で定義できます。 次の例に示すように、配列を宣言するときにサイズを指定することができます。  
  
 [!code-vb[VbVbalrArrays#12](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#12)]  
  
 また、次の例に示すように、 `New` 句を使用して配列を作成するときにサイズを指定することもできます。  
  
 [!code-vb[VbVbalrArrays#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#11)]  
  
 既存の配列がある場合は、 `Redim` ステートメントを使用してサイズを再定義できます。 `Redim` ステートメントでは、配列に格納されている値を保持するように指定することも、空の配列を作成するように指定することもできます。 次に、 `Redim` ステートメントを使用して既存の配列のサイズを変更する例をいくつか示します。  
  
 [!code-vb[VbVbalrArrays#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#13)]  
  
 詳細については、「[ReDim ステートメント](../../../../visual-basic/language-reference/statements/redim-statement.md)」を参照してください。  
  
##  <a name="BKMK_StoringValues"></a> 配列への値の格納  
 配列のそれぞれの位置には、 `Integer`型のインデックスを使用してアクセスできます。 かっこで囲まれたインデックスを使用して配列のそれぞれの位置を参照することで、配列の値を格納および取得することができます。 多次元配列のインデックスはコンマ (,) で区切ります。 配列の次元ごとに 1 つのインデックスが必要です。 配列に値を格納するステートメントの例を示します。  
  
 [!code-vb[VbVbalrArrays#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#5)]  
  
 配列から値を取得するステートメントの例を示します。  
  
 [!code-vb[VbVbalrArrays#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#6)]  
  
##  <a name="BKMK_Populating"></a> 配列への初期値の取り込み  
 配列リテラルを使用すると、初期値のセットを含む配列を作成できます。 配列リテラルは、中かっこ (`{}`) で囲んだ値のコンマ区切りの一覧で構成されます。  
  
 配列リテラルを使用して配列を作成する場合、配列の型を指定するか、型の推定を使用して配列の型を決定することができます。 この 2 つの方法を次のコードに示します。  
  
 [!code-vb[VbVbalrCollectionInitializers#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#3)]  
  
 型の推定を使用する場合、配列の型は、配列リテラルに指定された値の一覧の中で最も優先度の高い型によって決まります。 最も優先度の高い型は、配列リテラル内の他のすべての型から拡大変換できる一意の型です。 この一意の型を特定できない場合、最も優先度の高い型は、配列内の他のすべての型から縮小変換できる一意の型になります。 これらの一意の型をどちらも特定できない場合は、 `Object`が最も優先度の高い型になります。 たとえば、配列リテラルに指定された値の一覧に `Integer`型、 `Long`型、および `Double`型の値が含まれている場合、結果の配列の型は `Double`です。 `Integer` と `Long` は `Double`にのみ拡大変換されます。 そのため、 `Double` が最も優先度の高い型になります。 詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。 これらの推定規則は、クラス メンバーで定義されたローカル変数である配列についての型の推定に適用されます。 クラス レベルの変数を作成するときに配列リテラルを使用することはできますが、クラス レベルで型の推定を使用することはできません。 そのため、クラス レベルで指定された配列リテラルでは、配列リテラルに指定された値の型は `Object`型であると推論されます。  
  
 配列リテラルを使用して作成した配列の要素の型を明示的に指定することができます。 この場合、配列リテラル内の値を配列の要素の型に拡大変換する必要があります。 整数の一覧から `Double` 型の配列を作成するコード例を次に示します。  
  
 [!code-vb[VbVbalrCollectionInitializers#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#4)]  
  
###  <a name="BKMK_NestedArrayLiterals"></a> 入れ子になった配列リテラル  
 入れ子になった配列リテラルを使用すると、多次元配列を作成できます。 入れ子になった配列リテラルに含める次元および次元数 (ランク) は、結果の配列と一致する必要があります。 配列リテラルを使用して整数の 2 次元配列を作成するコード例を次に示します。  
  
 [!code-vb[VbVbalrCollectionInitializers#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#7)]  
  
 上記の例では、入れ子になった配列リテラル内の要素の数が一致しないとエラーが発生します。 また、2 次元以外の配列変数が明示的に宣言された場合もエラーが発生します。  
  
> [!NOTE]
>  入れ子になった配列リテラルで異なる次元を指定することによるエラーを回避するには、内側の配列をかっこで囲みます。 次のコードに示すようにかっこで囲むと、配列リテラル式の評価が実行され、そこで得られた値が外側の配列リテラルで使用されます。  
  
 [!code-vb[VbVbalrCollectionInitializers#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#11)]  
  
 入れ子になった配列リテラルを使用して多次元配列を作成する場合、型の推定を使用できます。 型の推定を使用すると、推定される型は、入れ子レベルのすべての配列リテラルに含まれるすべての値の中で最も優先度の高い型になります。 `Double` 型と `Integer` 型の値から `Double`型の 2 次元配列を作成するコード例を次に示します。  
  
 [!code-vb[VbVbalrCollectionInitializers#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#8)]  
  
 他の例については、「[方法: Visual Basic で配列変数を初期化する](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)」を参照してください。  
  
##  <a name="BKMK_Iterating"></a> 配列の反復処理  
 配列を反復処理するときには、配列の各要素に、最もインデックスが小さいものから順番にアクセスします。  
  
 次の例では、[For...Next ステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md)を使用して 1 次元配列を反復処理します。 <xref:System.Array.GetUpperBound%2A> メソッドでは、インデックスが保持できる一番高い値が返されます。 一番低いインデックス値は常に 0 です。  
  
 [!code-vb[VbVbalrArrays#41](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#41)]  
  
 次の例では、 `For...Next` ステートメントを使用して多次元配列を反復処理します。 <xref:System.Array.GetUpperBound%2A> メソッドには、次元を指定するパラメーターがあります。 `GetUpperBound(0)` は最初の次元の最も大きいインデックス値を返し、 `GetUpperBound(1)` は 2 番目の次元の最も大きいインデックス値を返します。  
  
 [!code-vb[VbVbalrArrays#42](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#42)]  
  
 次の例では、[For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)を使用して 1 次元配列を反復処理します。  
  
 [!code-vb[VbVbalrArrays#43](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#43)]  
  
 次の例では、 `For Each...Next` ステートメントを使用して多次元配列を反復処理します。 ただし、 `For…Next` ステートメントを使用するより、前の例のように、入れ子になった `For Each…Next` ステートメントを使用した方が、多次元配列の要素をより細かく制御できます。  
  
 [!code-vb[VbVbalrArrays#44](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#44)]  
  
##  <a name="BKMK_ReturnValues"></a> 戻り値およびパラメーターとしての配列  
 `Function` プロシージャから配列を返すには、[Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)の戻り値の型として配列のデータ型と次元数を指定します。 関数内で、同じデータ型と次元数を持つローカルの配列変数を宣言します。 [Return ステートメント](../../../../visual-basic/language-reference/statements/return-statement.md)には、かっこを使用せずにローカルの配列変数を含めます。  
  
 配列を `Sub` プロシージャまたは `Function` プロシージャのパラメーターとして指定するには、パラメーターを配列として定義して、データ型と次元数を指定します。 プロシージャの呼び出しで、データ型と次元数が同じ配列変数を渡します。  
  
 次の例では、 `GetNumbers` 関数が `Integer()`を返します。 この配列型は、 `Integer`型の 1 次元配列です。 `ShowNumbers` プロシージャは、 `Integer()` の引数を受け取ります。  
  
 [!code-vb[VbVbalrArrays#51](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#51)]  
  
 次の例では、 `GetNumbersMultiDim` 関数が `Integer(,)`を返します。 この配列型は、 `Integer`型の 2 次元配列です。  `ShowNumbersMultiDim` プロシージャは、 `Integer(,)` の引数を受け取ります。  
  
 [!code-vb[VbVbalrArrays#52](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#52)]  
  
##  <a name="BKMK_JaggedArrays"></a> ジャグ配列  
 他の配列を要素として保持する配列を、配列の配列またはジャグ配列と呼びます。 ジャグ配列と、ジャグ配列の各要素は、1 次元でも多次元でもかまいません。 アプリケーションのデータ構造は、2 次元の配列であっても四角形の 2 次元配列ではない場合があります。  
  
 次の例には、各要素が日の配列である月の配列が含まれています。 月によって日数が異なるため、月要素は四角形の 2 次元配列を形成しません。 そのため、多次元配列の代わりにジャグ配列が使用されています。  
  
 [!code-vb[VbVbalrArrays#21](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#21)]  
  
##  <a name="BKMK_ZeroLength"></a> 長さ 0 の配列  
 要素を持たない配列は、長さ 0 の配列と呼ばれます。 長さ 0 の配列を保持する変数の値は、 `Nothing`ではありません。 要素を持たない配列を作成するには、次の例のように配列の次元のいずれかを -1 と宣言します。  
  
 [!code-vb[VbVbalrArrays#14](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#14)]  
  
 次のような場合に、長さ 0 の配列を作成する必要があります。  
  
-   <xref:System.NullReferenceException> 例外を発生させずにコードで <xref:System.Array> クラスのメンバー (<xref:System.Array.Length%2A>、<xref:System.Array.Rank%2A> など) にアクセスしたり [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 関数 (<xref:Microsoft.VisualBasic.Information.UBound%2A> など) を呼び出したりする必要がある場合。  
  
-   特別なケースですが、`Nothing` をチェックする必要性をなくすことによって利用側のコードを簡素化する場合。  
  
-   コードで、長さ 0 の配列を 1 つ以上のプロシージャに渡す必要があるアプリケーション プログラミング インターフェイス (API: Application Programming Interface) とやり取りする場合、または API の 1 つ以上のプロシージャから長さ 0 の配列が返される場合。  
  
##  <a name="BKMK_ArraySize"></a> 配列のサイズ  
 配列のサイズは、そのすべての次元の長さの積です。 これは、現在配列に含まれている要素の総数を表します。  
  
 次の例では 3 次元配列を宣言しています。  
  
```  
Dim prices(3, 4, 5) As Long  
```  
  
 変数 `prices` の配列の全体のサイズは、(3 + 1) x (4 + 1) x (5 + 1) = 120 です。  
  
 配列のサイズは、<xref:System.Array.Length%2A> プロパティを使用して確認できます。 多次元配列の各次元の長さは、<xref:System.Array.GetLength%2A> メソッドを使用して確認できます。  
  
 配列変数のサイズを変更するには、新しい配列オブジェクトを割り当てるか、`ReDim` ステートメントを使用します。  
  
 配列のサイズを扱う際に考慮する必要がある点がいくつかあります。  
  
|||  
|---|---|  
|次元の長さ|各次元のインデックスは 0 ベースであり、範囲は 0 から上限です。 したがって、次元の長さは、その次元に対する宣言された上限よりも 1 だけ大きくなります。|  
|長さの制限|配列のすべての次元の長さは、`Integer` データ型の最大値に制限されます。最大値は (2 ^ 31) - 1 です。 しかし、配列のサイズの総数も、システムで利用できるメモリによって制限されます。 利用できる RAM の容量を超える配列を初期化する場合、共通言語ランタイムは <xref:System.OutOfMemoryException> 例外をスローします。|  
|サイズおよび要素のサイズ|配列のサイズは、その要素のデータ型には依存しません。 サイズは常に、使用するストレージのバイト数ではなく、要素の合計数を表します。|  
|メモリの使用量|配列がどのようにメモリに格納されるかに関して、前提を置くことは安全ではありません。 ストレージは、プラットフォームのデータ幅が異なると変わります。したがって、同じ配列でも、32 ビットのシステムよりも 64 ビットのシステムの方が多くのメモリを使用します。 配列を初期化すると、システム構成に応じて、要素をできるだけ近くに集めるように、またはすべてがハードウェア自体の境界に合致するように、共通言語ランタイム (CLR: Common Language Runtime) によってストレージが割り当てられます。 また、配列は制御情報のためにストレージのオーバーヘッドを必要とします。このオーバーヘッドは、次元が追加されるごとに増加します。|  
  
##  <a name="BKMK_ArrayTypes"></a> 配列の型および他の型  
 すべての配列にデータ型がありますが、要素のデータ型とは異なります。 すべての配列を包括する 1 つのデータ型はありません。 代わりに、配列のデータ型は、配列の次元数 ( *ランク*) と配列の要素のデータ型によって決まります。 ランクと要素のデータ型が一致しない限り、2 つの配列変数が同じデータ型を持つと見なされることはありません。 配列の各次元の長さは、配列のデータ型には影響しません。  
  
 すべての配列は、<xref:System.Array?displayProperty=fullName> クラスから継承しています。また、`Array` 型として変数を宣言できますが、`Array` 型の配列は作成できません。 また、[ReDim ステートメント](../../../../visual-basic/language-reference/statements/redim-statement.md) は、`Array` 型として宣言された変数上では使用できません。 これらの理由やタイプ セーフを考慮して、すべての配列を、前の例の `Integer` などの特定の型として宣言することをお勧めします。  
  
 いくつかの方法で、配列またはその要素のいずれかのデータ型を知ることができます。  
  
-   変数の <xref:System.Object.GetType%2A?displayProperty=fullName> メソッドを呼び出して、実行時型の変数の <xref:System.Type> オブジェクトを取得できます。 <xref:System.Type> オブジェクトでは、プロパティおよびメソッドに詳細情報が保持されます。  
  
-   変数を <xref:Microsoft.VisualBasic.Information.TypeName%2A> 関数に渡して、実行時型の名前が含まれる `String` を取得できます。  
  
-   変数を <xref:Microsoft.VisualBasic.Information.VarType%2A> 関数に渡して、変数の型の分類を表す `VariantType`値を受け取ることができます。  
  
 `TypeName` 関数を呼び出して配列の型と配列の要素の型を確認する例を次に示します。 配列の型は `Integer(,)` で、配列の要素の型は `Integer`です。  
  
 [!code-vb[VbVbalrArrays#15](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#15)]  
  
##  <a name="BKMK_Collections"></a> 配列の代わりとしてのコレクション  
 配列は、数が固定されている厳密に型指定されたオブジェクトの作成および処理に最も適しています。 コレクションは、オブジェクトのグループをより柔軟に処理できます。 配列の場合とは違って、コレクションで扱うオブジェクトのグループは、アプリケーションのニーズの変化に応じて動的に拡大および縮小できます。  
  
 配列のサイズを変更する必要がある場合は、[ReDim ステートメント](../../../../visual-basic/language-reference/statements/redim-statement.md)を使用する必要があります。 これを行うと、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] により新しい配列が作成され、前の配列が解放されて廃棄されます。 これには、実行時間がかかります。 したがって、操作を行う項目の数が頻繁に変更される場合、または必要な項目の最大数を予測できない場合、コレクションを使用するとパフォーマンスが向上します。  
  
 コレクションによっては、コレクションに含まれるオブジェクトのキーを割り当てると、そのキーを使用してオブジェクトを迅速に取り出すことができます。  
  
 含まれる要素が 1 つのデータ型だけのコレクションの場合は、<xref:System.Collections.Generic?displayProperty=fullName> 名前空間のクラスのいずれかを使用できます。 ジェネリック コレクションでは、タイプ セーフが強制されるため、他のデータ型を追加することはできません。 ジェネリック コレクションから要素を取得する場合は、データ型を判断したり、変換したりする必要はありません。  
  
 コレクションの詳細については、「[コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)」を参照してください。  
  
### <a name="example"></a>例  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のジェネリック クラス <xref:System.Collections.Generic.List%601?displayProperty=fullName> を使用して、`Customer` オブジェクトの一覧コレクションを作成する例を次に示します。  
  
 [!code-vb[VbVbalrArrays#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#1)]  
  
 `CustomerFile` コレクションの宣言により、 `Customer`型だけの要素を含むことができることを指定します。 また、200 要素分の初期容量も用意されています。 `AddNewCustomer` プロシージャにより、新しい要素の有効性がチェックされ、コレクションに追加されます。 `PrintCustomers` プロシージャでは、コレクションを走査し、その要素を表示するために、 `For Each` ループが使用されます。  
  
## <a name="related-topics"></a>関連トピック  
  
|用語|定義|  
|----------|----------------|  
|[Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|配列のランクと次元について説明します。|  
|[方法: Visual Basic で配列変数を初期化する](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|配列に初期値を設定する方法について説明します。|  
|[方法: 配列を並べ替える (Visual Basic)](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|配列の要素をアルファベット順に並べ替える方法について説明します。|  
|[方法 : 配列を別の配列に代入する](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|配列を別の配列変数に代入するときの手順と規則を説明します。|  
|[配列のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|配列を使用しているときに発生する一般的な問題について説明します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Array>   
 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [ReDim ステートメント](../../../../visual-basic/language-reference/statements/redim-statement.md)

