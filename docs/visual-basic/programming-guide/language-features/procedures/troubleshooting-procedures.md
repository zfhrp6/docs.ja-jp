---
title: "プロシージャのトラブルシューティング (Visual Basic) |Microsoft ドキュメント"
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
- troubleshooting Visual Basic, procedures
- procedures, troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures, about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: a5445d6da982e4eea5b1047505e4bee3380ed472
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-procedures-visual-basic"></a>プロシージャのトラブルシューティング (Visual Basic)
ここでは、プロシージャを使用する場合に発生することが一般的な問題についてを説明します。  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Function プロシージャから、配列型を返す  
 場合、`Function`配列のデータ型を返し、使用することはできません、`Function`配列の要素の値を格納する名前。 これを行うしようとすると、コンパイラによって呼び出しとして、`Function`です。 次の例では、コンパイラ エラーを生成します。  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 ステートメント`allOnes(i) = 1`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`無効なデータ型の引数を持つ (シングルトン`Integer`の代わりに、`Integer`配列)。 ステートメント`Return allOnes()`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`引数なしでします。  
  
 **適切なアプローチ。**が返される配列の要素を変更できるようにするには、ローカル変数として内部の配列を定義します。 次の例では、コンパイル エラーが発生します。  
  
 [!code-vb[VbVbcnProcedures #&66;](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>引数は変更されていないプロシージャ呼び出しで  
 呼び出し元のコードで引数を基になるプログラミングの要素を変更する手順を許可する場合は、参照によって渡す必要があります。 値渡しで渡す場合でも、プロシージャが参照型の引数の要素をアクセスできます。  
  
-   **変数を基になる**します。 基になる変数要素自体の値を置き換えるための手順を許可するように、プロシージャには、パラメーターを宣言する必要があります[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。 また、呼び出し元のコードいない引数かっこで囲んでくださいをオーバーライドするため、`ByRef`渡す機能します。  
  
-   **型の要素を参照する**です。 パラメーターを宣言する場合は、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャは、基になる変数要素自体を変更できません。 ただし、引数が参照型の場合、変数の値を置き換えることができない場合でも、プロシージャは、ポイントをするには、オブジェクトのメンバー変更できます。 たとえば、引数が、配列変数の場合は、プロシージャは、新しい配列を割り当てることはできませんが、1 つまたは複数の要素を変更することができます。 変更された要素は、呼び出し元のコードで基になる配列変数に反映されます。  
  
 次の例では、その要素の値によって、配列変数を実行して、操作を&2; つの手順を定義します。 プロシージャ`increase`単純に各要素に&1; を追加します。 プロシージャ`replace`パラメーターに新しい配列を割り当てます`a()`し、各要素に&1; を追加します。 ただし、再割り当ては変わりません呼び出し元のコードで基になる配列変数のため`a()`が宣言されている`ByVal`します。  
  
 [!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures #&38;](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 に対する呼び出しを次の例`increase`と`replace`です。  
  
 [!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。 `n` 、参照型では、`increase`が渡される場合でも、そのメンバーを変更できます`ByVal`します。  
  
 2 番目`MsgBox`表示を呼び出して"目後: 11、21、31、41"です。 `n`は`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることで。 ときに`replace`配列の新しいインスタンスを作成`k`し、ローカル変数に代入`a`への参照が失われた`n`して呼び出し元のコードに渡されます。 メンバーをインクリメントして`a`、ローカル配列のみ`k`が影響を受けます。  
  
 **適切なアプローチ。**を基になる変数要素自体を変更するには、参照渡しで渡します。 次の例の宣言で、変更を表示する`replace`を呼び出し元のコードの別の&1; つの配列を置き換えるようになります。  
  
 [!code-vb[VbVbcnProcedures #&64;](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>オーバー ロードを定義できません。  
 プロシージャのオーバー ロードされたバージョンを定義する場合は、同じ名前で別の署名を使用する必要があります。 コンパイラは、同じシグネチャを持つオーバー ロードの宣言を区別することはできません、エラーを生成します。  
  
 *署名*プロシージャのプロシージャ名とパラメーター リストによって決定されます。 各オーバー ロードは、他のすべてのオーバー ロードと同じ名前である必要がありますが、署名の他のコンポーネントの少なくとも&1; つにそれらすべてを異なる必要があります。 詳細については、次を参照してください。[プロシージャのオーバー ロード](./procedure-overloading.md)します。  
  
 次の項目場合でも、パラメーター リストには関係ないコンポーネントを示しますプロシージャの署名。  
  
-   プロシージャ修飾子のキーワードなど`Public`、`Shared`と`Static`  
  
-   パラメーター名  
  
-   パラメーター修飾子のキーワードなど`ByRef`と`Optional`  
  
-   (変換演算子) を除く、戻り値のデータ型  
  
 プロシージャをオーバー ロードするだけで&1; つ以上前の項目のことはできません。  
  
 **適切なアプローチ。**プロシージャのオーバー ロードを定義できるようにするには、署名を変更する必要があります。 同じ名前を使用する必要がありますので、数、順序、またはパラメーターのデータ型を変更しなければなりません。 ジェネリック プロシージャでは、型パラメーターの数を変更できます。 変換演算子で ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md))、戻り値の型を変更することができます。  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>省略可能な解像度と ParamArray 引数をオーバー ロードします。  
 1 つまたは複数のプロシージャをオーバー ロードは場合[省略可能](../../../../visual-basic/language-reference/modifiers/optional.md)パラメーターまたは[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーターのいずれかの複製避ける必要があります、*暗黙のオーバー ロード*します。 詳細については、次を参照してください。[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)します。  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>オーバー ロードされたプロシージャの間違ったバージョンの呼び出し  
 プロシージャにいくつかのオーバー ロードされたバージョンがある場合、すべてのパラメーター リストを理解しておく理解しておいてください方法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]オーバー ロード間の呼び出しを解決します。 それ以外の場合、意図したものではないオーバー ロードを呼び出す可能性があります。  
  
 どのオーバー ロードを呼び出そうとするを決定するには、次の規則に従うように注意します。  
  
-   引数、および正しい順序で、正確な数を指定します。  
  
-   理想的には、引数には、対応するパラメーターとまったく同じデータ型が必要です。 いずれの場合は、各引数のデータ型は、対応するパラメーターに拡大変換する必要があります。 これは、true の場合でも、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)に設定`Off`します。 オーバー ロードをオーバー ロードする引数リストから任意の縮小変換が必要な場合は、呼び出される対象ではありません。  
  
-   拡大変換で必要な引数を指定する場合は、対応するパラメーターのデータ型にできるだけ近くにそのデータ型を確認します。 2 つまたは複数のオーバー ロードは、引数のデータ型を受け取る、コンパイラは、拡大の最低限の呼び出しのオーバー ロードの呼び出しを解決します。  
  
 データ型の不一致の可能性を低くにを使用して、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)引数を指定するとき、変換キーワードです。  
  
### <a name="overload-resolution-failure"></a>オーバー ロードの解決に失敗しました。  
 オーバー ロードされたプロシージャを呼び出すときに、コンパイラは、オーバー ロードの&1; つだけを削除しようとします。 成功した場合は、そのオーバー ロードの呼び出しを解決します。 すべてのオーバー ロードを排除または、オーバー ロードの候補を&1; つを減らすことができない場合は、エラーを生成します。  
  
 次の例では、オーバー ロードの解決プロセスを示します。  
  
 [!code-vb[VbVbcnProcedures #&62;](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures #&63;](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 最初の呼び出しで、コンパイラが最初のオーバー ロードを排除の最初の引数の型 (`Short`) に対応するパラメーターの型を変更して (`Byte`)。 次に除去&3; 番目のオーバー ロードは、2 番目のオーバー ロードで各引数の型 (`Short`と`Single`)&3; 番目のオーバー ロードでは、対応する型に拡大変換 (`Integer`と`Single`)。 2 番目のオーバー ロードが必要な拡大が少ないので、コンパイラは、呼び出しの使用します。  
  
 2 番目の呼び出しで、コンパイラは縮小に基づいてオーバー ロードのいずれかを取り除くことはできません。 除外した引数型の&2; 番目のオーバー ロードを呼び出すことがあるため、最初の呼び出しと同様に、同じ理由から&3; 番目のオーバー ロードを除外します。 ただし、コンパイラは、最初と&2; 番目のオーバー ロードの間で解決できません。 もう一方で対応する型を拡張する&1; つの定義済みパラメーターの型を持つ各 (`Byte`に`Short`が`Single`に`Double`)。 そのため、コンパイラは、オーバー ロードの解決エラーを生成します。  
  
 **適切なアプローチ。**あいまいさなしのオーバー ロードされたプロシージャを呼び出すには、次のように使用します。 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)パラメーターの型への引数のデータ型を一致するようにします。 次の例では、呼び出しを`z`を強制的に&2; 番目のオーバー ロードを解決します。  
  
 [!code-vb[VbVbcnProcedures #&65;](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>省略可能な解像度と ParamArray 引数をオーバー ロードします。  
 最後のパラメーターを宣言する点を除いて、プロシージャの&2; つのオーバー ロードと同じシグネチャを持つ場合[省略可能](../../../../visual-basic/language-reference/modifiers/optional.md)いずれかでと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 、もう一方で、コンパイラは、最も近いに従ってそのプロシージャを呼び出すを解決します。 詳細については、次を参照してください。[オーバー ロード解決](./overload-resolution.md)します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Sub プロシージャ](./sub-procedures.md)   
 [Function プロシージャ](./function-procedures.md)   
 [プロパティ プロシージャ](./property-procedures.md)   
 [演算子プロシージャ](./operator-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [プロシージャのオーバー ロード](./procedure-overloading.md)   
 [プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)   
 [オーバーロードの解決](./overload-resolution.md)
