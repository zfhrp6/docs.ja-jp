---
title: "オーバー ロードの解決 (Visual Basic) |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- overload resolution
- procedures, overloading
- procedures, calling
- procedure overloading, overload resolution
- signatures, procedure
- overloads, resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
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
ms.openlocfilehash: 0de3a603fa84a72018a566f6e7182b45e53ec89e
ms.lasthandoff: 03/13/2017

---
# <a name="overload-resolution-visual-basic"></a>オーバーロードの解決法 (Visual Basic)
ときに、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラは、いくつかのオーバー ロードされたバージョンで定義されているプロシージャの呼び出しを検出すると、コンパイラは、オーバー ロードを呼び出すを決定する必要があります。 次の手順を実行することによってこれが行われます。  
  
1.  **ユーザー補助機能です。** 呼び出し元のコードの呼び出しを防止するアクセス レベルを持つオーバー ロードを除外します。  
  
2.  **パラメーターの数。** 呼び出しで指定された数と異なる数のパラメーターが定義されているオーバー ロードを除外します。  
  
3.  **パラメーターのデータ型。** コンパイラは、拡張メソッドよりインスタンス メソッドを優先します。 拡大に合わせてプロシージャの呼び出しの変換だけが必要な任意のインスタンス メソッドが見つかった場合は、すべての拡張メソッドは削除され、インスタンス メソッドの候補をコンパイラが続行します。 このようなインスタンス メソッドが見つからない場合は、インスタンスと拡張メソッドの両方で続行します。  
  
     この手順で、オーバー ロードで定義されているパラメーターの型への呼び出しの引数のデータ型を変換できませんオーバー ロードを除外します。  
  
4.  **縮小変換です。** 定義されたパラメーターの型への呼び出しの引数の型から縮小変換を必要なオーバー ロードを除外します。 これは、該当の型チェックを切り替えるかどうか ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`または`Off`です。  
  
5.  **最小の拡大。** コンパイラは、ペアで残りのオーバー ロードを考慮します。 各ペアに対して定義されているパラメーターのデータ型を比較します。 すべてのオーバー ロードのいずれかの型は、もう一方で対応する型に拡大する場合、コンパイラは、後者を除外します。 つまり、最小限の拡大を必要とするオーバー ロードを保持します。  
  
6.  **1 つの候補です。** オーバー ロードを&1; つだけまでのペアがそのまま残り、オーバー ロードし、そのオーバー ロードの呼び出しを解決することを検討して続行します。 コンパイラは、候補を&1; つのオーバー ロードを減らすことができない、エラーを生成します。  
  
 次の図は、一連のオーバー ロードされたバージョンを呼び出すのどれかを判断するプロセスを示しています。  
  
 ![オーバー ロードの解決プロセスのフロー図](./media/overloadres.gif "OverloadRes")  
オーバー ロードされたバージョンを解決します。  
  
 次の例では、このオーバー ロードの解決プロセスを示します。  
  
 [!code-vb[VbVbcnProcedures #&62;](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&63;](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 最初の呼び出しで、コンパイラが最初のオーバー ロードを排除の最初の引数の型 (`Short`) に対応するパラメーターの型を変更して (`Byte`)。 次に除去&3; 番目のオーバー ロードは、2 番目のオーバー ロードで各引数の型 (`Short`と`Single`)&3; 番目のオーバー ロードでは、対応する型に拡大変換 (`Integer`と`Single`)。 2 番目のオーバー ロードが必要な拡大が少ないので、コンパイラは、呼び出しの使用します。  
  
 2 番目の呼び出しで、コンパイラは縮小に基づいてオーバー ロードのいずれかを取り除くことはできません。 除外した引数型の&2; 番目のオーバー ロードを呼び出すことがあるため、最初の呼び出しと同様に、同じ理由から&3; 番目のオーバー ロードを除外します。 ただし、コンパイラは、最初と&2; 番目のオーバー ロードの間で解決できません。 もう一方で対応する型を拡張する&1; つの定義済みパラメーターの型を持つ各 (`Byte`に`Short`が`Single`に`Double`)。 そのため、コンパイラは、オーバー ロードの解決エラーを生成します。  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>省略可能なオーバー ロードと ParamArray 引数  
 最後のパラメーターを宣言する点を除いて、プロシージャの&2; つのオーバー ロードと同じシグネチャを持つ場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)いずれかでと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 、もう一方で、コンパイラは解決そのプロシージャを呼び出す次のようにします。  
  
|呼び出しが最後の引数として指定した場合|コンパイラは最後の引数として宣言するオーバー ロードの呼び出しを解決します。|  
|---|---|  
|値なし (引数を省略すると)|`Optional`|  
|1 つの値|`Optional`|  
|コンマ区切りの一覧で、2 つ以上の値|`ParamArray`|  
|(空の配列を含む) 任意の長さの配列|`ParamArray`|  
  
## <a name="see-also"></a>関連項目  
 [省略可能なパラメーター](./optional-parameters.md)   
 [パラメーター配列](./parameter-arrays.md)   
 [プロシージャのオーバー ロード](./procedure-overloading.md)   
 [トラブルシューティングの手順](./troubleshooting-procedures.md)   
 [方法: プロシージャの複数のバージョンを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)   
 [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)   
 [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)   
 [オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [拡張メソッド](./extension-methods.md)
