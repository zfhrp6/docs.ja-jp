---
title: プロシージャのトラブルシューティング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: f66e7f7444f2d3b1bb58bae6008f8896c81c2f76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655520"
---
# <a name="troubleshooting-procedures-visual-basic"></a>プロシージャのトラブルシューティング (Visual Basic)
このページには、プロシージャを使用する場合に発生する可能性がある一般的な問題が一覧表示されます。  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Function プロシージャから配列型を返す  
 場合、`Function`プロシージャは、配列のデータ型を返しますでは使用できません、`Function`値を格納する配列の要素の名前。 これを行うしようとすると、コンパイラによって呼び出しとして、`Function`です。 次の例では、コンパイラ エラーを生成します。  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 ステートメント`allOnes(i) = 1`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`不適切なデータ型の引数を持つ (シングルトン`Integer`の代わりに、`Integer`配列)。 ステートメント`Return allOnes()`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`引数なしでします。  
  
 **適切なアプローチ:** が返される配列の要素を変更できるようにするには、ローカル変数として内部の配列を定義します。 次の例がエラーなしでコンパイルします。  
  
 [!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>変更されていない引数によってプロシージャの呼び出し  
 プロシージャは呼び出し元のコードで引数の基になるプログラミング要素の変更を許可する場合は、参照渡しで渡す必要があります。 値渡しで渡す場合でも、プロシージャが参照型の引数の要素をアクセスできます。  
  
-   **変数を基になる**です。 基になる変数要素自体の値を変更する手順は、プロシージャには、パラメーターを宣言する必要があります[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)です。 また、呼び出し元のコードいない引数かっこで囲んでくださいをオーバーライドするため、`ByRef`引き渡し方法です。  
  
-   **型の要素を参照**です。 パラメーターを宣言する場合[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャは、基になる変数要素自体を変更できません。 ただし、引数が参照型の場合、変数の値を置き換えることができない場合でも、プロシージャは、ポイントをするには、オブジェクトのメンバー変更できます。 たとえば、引数が、配列変数の場合は、プロシージャは、新しい配列を割り当てることはできませんが、1 つまたは複数の要素を変更することができます。 変更された要素は、基になる配列内の変数呼び出し元のコードに反映されます。  
  
 次の例では、その要素の値によって、配列変数を行い、操作を 2 つの手順を定義します。 プロシージャ`increase`単に各要素に 1 を追加します。 プロシージャ`replace`パラメーターに新しい配列を割り当てます`a()`し、各要素に 1 を追加します。 ただし、再割り当てには影響しません、基になる配列内の変数呼び出し元のコードのため`a()`が宣言されている`ByVal`です。  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 次の例は、呼び出しを`increase`と`replace`です。  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。 `n` 、参照型では、`increase`渡される場合でも、そのメンバーを変更できます`ByVal`です。  
  
 2 番目`MsgBox`表示を呼び出して"目後: 41、11、21、31"です。 `n`渡される`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることによってです。 ときに`replace`配列の新しいインスタンスを作成`k`し、ローカル変数に代入`a`への参照が失われた`n`呼び出し元のコードで渡される入力します。 メンバーをインクリメントするときに`a`、ローカルの配列のみ`k`が影響を受けます。  
  
 **適切なアプローチ:** を基になる変数要素自体を変更するには、参照渡しで渡します。 次の例では、変更を示しますの宣言で`replace`呼び出し元のコードの別の 1 つの配列を置き換えることができます。  
  
 [!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>オーバー ロードを定義できません。  
 プロシージャのオーバー ロードされたバージョンを定義する場合は、異なるシグネチャが同じ名前を使用する必要があります。 コンパイラは、同じシグネチャを持つオーバー ロードの宣言を区別することはできません、エラーが生成されます。  
  
 *署名*プロシージャのプロシージャ名とパラメーター リストによって決定されます。 各オーバー ロードは、他のすべてのオーバー ロードと同じ名前を持つ必要がありますが、シグネチャの他のコンポーネントの少なくとも 1 つにそれらのすべてを異なる必要があります。 詳細については、次を参照してください。[プロシージャのオーバー ロード](./procedure-overloading.md)です。  
  
 次の項目を場合でも、パラメーター リストには関係ないコンポーネントを示します、プロシージャの署名。  
  
-   プロシージャ修飾子キーワードなど`Public`、 `Shared`、および `Static`  
  
-   パラメーター名  
  
-   パラメーター修飾子キーワードなど`ByRef`と `Optional`  
  
-   (変換演算子) を除く、戻り値のデータ型  
  
 1 つ以上の前の項目のみプロシージャをオーバー ロードすることはできません。  
  
 **適切なアプローチ:** プロシージャのオーバー ロードを定義できるようにするには、署名を変更する必要があります。 同じ名前を使用する必要があるために、数、順序、またはパラメーターのデータ型を変更しなければなりません。 ジェネリック プロシージャでは、型パラメーターの数を変更できます。 変換演算子で ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md))、戻り値の型を変更できます。  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>省略可能な解像度と ParamArray 引数にオーバー ロードします。  
 場合は 1 つまたは複数のプロシージャをオーバー ロードは[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)パラメーターまたは[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、複製のいずれかの回避する必要があります、*暗黙のオーバー ロード*です。 詳細については、次を参照してください。[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)です。  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>オーバー ロードされたプロシージャの間違ったバージョンの呼び出し  
 プロシージャにいくつかのオーバー ロードされたバージョンがある場合、すべてのパラメーター リストに理解して、Visual Basic での通話を複数のオーバー ロードの解決方法を理解してください。 それ以外の場合、意図したもの以外オーバー ロードを呼び出す可能性があります。  
  
 どのオーバー ロードを呼び出したいを特定する場合は、次の規則に注意してください。  
  
-   引数、および正しい順序では、正しい番号を指定します。  
  
-   理想的には、引数には、対応するパラメーターとまったく同じデータ型が必要です。 いずれの場合は、各引数のデータ型が、対応するパラメーターに拡大変換する必要があります。 これは、true を使用しても、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)'éý'`Off`です。 オーバー ロードをオーバー ロードする、引数リストから縮小変換を必要とする場合は、呼び出される対象となるではありません。  
  
-   拡大変換を必要とする引数を指定する場合は、対応するパラメーターのデータ型にできるだけ近いデータ型を確認します。 2 つまたは複数のオーバー ロードは、引数のデータ型を受け取る、コンパイラは拡大量の最小のオーバー ロードへの呼び出しを解決します。  
  
 使用してデータ型の不一致の可能性を低くことができます、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)引数を指定するとき、変換キーワード。  
  
### <a name="overload-resolution-failure"></a>オーバー ロードの解決に失敗しました。  
 オーバー ロードされたプロシージャを呼び出すときに、コンパイラは、オーバー ロードの 1 つだけを削除しようとします。 成功した場合は、そのオーバー ロードへの呼び出しを解決します。 すべてのオーバー ロードがなく、オーバー ロード候補を 1 つを減らすことはできない場合や、エラーを生成します。  
  
 次の例では、オーバー ロードの解決プロセスを示します。  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 コンパイラがあるため最初のオーバー ロードを排除最初の呼び出しで最初の引数の型 (`Short`)、対応するパラメーターの型へ縮小変換 (`Byte`)。 次に除去 3 番目のオーバー ロードは、2 番目のオーバー ロードで各引数の型 (`Short`と`Single`) 3 番目のオーバー ロードでは、対応する型に拡大変換 (`Integer`と`Single`)。 2 番目のオーバー ロードが必要な小さい拡大ので、コンパイラは、呼び出しに使用します。  
  
 2 番目の呼び出しでは、コンパイラは縮小に基づいてオーバー ロードのいずれかで除去ことはできません。 引数の型の少ない拡大変換と 2 番目のオーバー ロードを呼び出すことがあるため最初の呼び出しと同様に、同じ理由から、3 番目のオーバー ロードを除外します。 ただし、コンパイラは、最初と 2 番目のオーバー ロードの解決できません。 それぞれが、他の対応する型に拡大する 1 つの定義済みパラメーターの型 (`Byte`に`Short`が`Single`に`Double`)。 そのため、コンパイラには、オーバー ロードの解決エラーが生成されます。  
  
 **適切なアプローチ:** にあいまいさを排除オーバー ロードされたプロシージャを呼び出すには、次のように使用します。 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)パラメーターの型引数のデータ型を一致するようにします。 次の例への呼び出しを示しています。`z`を強制的に 2 番目のオーバー ロードに解決します。  
  
 [!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>省略可能な解像度と ParamArray 引数にオーバー ロードします。  
 最後のパラメーターを宣言する点を除いて、プロシージャの 2 つのオーバー ロードが同じシグネチャを持つ場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)いずれかでと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)他のコンパイラがそのプロシージャの呼び出しを解決最も近いに従っています。 詳細については、次を参照してください。[オーバー ロードの解決](./overload-resolution.md)です。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Function プロシージャ](./function-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)  
 [オーバーロードの解決](./overload-resolution.md)
