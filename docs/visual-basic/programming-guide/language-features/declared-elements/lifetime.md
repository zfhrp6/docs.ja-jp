---
title: "Visual Basic における有効期間 |Microsoft ドキュメント"
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
- static variables, lifetime
- static variables, Visual Basic
- declared elements, lifetime
- Shared variable lifetime
- lifetime, declared elements
- lifetime, Visual Basic
- lifetime
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
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
ms.openlocfilehash: fa0cbdf4a8fe5e8fc41e4e4f373c79451fb7b75f
ms.lasthandoff: 03/13/2017

---
# <a name="lifetime-in-visual-basic"></a>Visual Basic における有効期間
*有効期間*宣言された要素は、一定時間その中に、使用可能です。 変数は、有効期間がある要素だけです。 この目的では、コンパイラは、プロシージャのパラメーターを処理し、変数の特殊なケースとして関数を返します。 変数の有効期間は、値を保持できる期間を表します。 その値をその有効期間を通じて変更できますが、いくつかの値を常に保持します。  
  
## <a name="different-lifetimes"></a>別の有効期間  
 A*メンバー変数*(プロシージャの外側のモジュール レベルで宣言された) が宣言された要素と同じ有効期間は、通常ができます。 クラスまたは構造体で宣言されている非共有変数は、クラスまたは構造体の宣言されているは、各インスタンスの別のコピーとして存在します。 このような各変数には、そのインスタンスと同じ有効期間があります。 ただし、`Shared`変数が有効期間は&1; つだけでは継続時間全体で、アプリケーションが実行されています。  
  
 A*ローカル変数*(プロシージャ内で宣言された) が宣言されているプロシージャの実行中にのみ存在します。 関数の戻り値とそのプロシージャのパラメーターにも当てはまります。 ただし、プロシージャが他のプロシージャを呼び出した場合は、呼び出されたプロシージャが実行中にローカル変数の値は保持します。  
  
## <a name="beginning-of-lifetime"></a>有効期間の開始  
 ローカル変数の有効期間は、制御が宣言されている手順を開始するときに開始されます。 プロシージャが開始されるとすぐには、すべてのローカル変数をそのデータ型の既定値に初期化を実行しています。 プロシージャが検出した場合、`Dim`を初期値を指定するステートメントにローカル変数に設定これらの値をコードではその他の値に既に割り当ていた場合でもです。  
  
 構造体変数の各メンバーは、そうでは別々 の変数として初期化されます。 同様に、配列変数の各要素は、個別に初期化されます。  
  
 プロシージャ内のブロック内で宣言された変数 (など、`For`ループ)、プロシージャへのエントリが初期化されています。 このような初期化を有効に、コードがこれまで、ブロックを実行するかどうか。  
  
## <a name="end-of-lifetime"></a>有効期間の終了  
 プロシージャが終了すると、そのローカル変数の値は保持されず、および[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のメモリを解放します。 次に、プロシージャを呼び出すとき、すべてのローカル変数が新しく作成して再初期化します。  
  
 クラスまたは構造体のインスタンスが終了すると、非共有変数には、そのメモリとその値が失われます。 クラスまたは構造体の新しいインスタンスごとでは、作成し、非共有変数を再初期化します。 ただし、`Shared`変数は、アプリケーションの実行が停止されるまで保持されます。  
  
## <a name="extension-of-lifetime"></a>有効期間の延長  
 ローカル変数を宣言する場合、`Static`キーワード、その有効期間は、プロシージャの実行時間より長い。 次の表は、プロシージャの宣言が期間を指定する方法を示しています、`Static`変数が存在します。  
  
|プロシージャの場所との共有|静的変数の有効期間を開始します。|静的変数の有効期間の終了|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|(既定では共有) モジュールで|初めてのプロシージャが呼び出されたとき|アプリケーションの実行が終了|  
|クラスでは、 `Shared` (手順は、インスタンスのメンバーではありません)|最初に、特定のインスタンスまたはクラスまたは構造体名自体のいずれかの手順が呼び出されます|アプリケーションの実行が終了|  
|クラスのインスタンスでない`Shared`(手順では、インスタンス メンバー)|初めてのプロシージャは、特定のインスタンスで呼び出されます|ガベージ コレクション (GC) のインスタンスを解放する場合|  
  
## <a name="static-variables-of-the-same-name"></a>同じ名前の静的変数  
 1 つ以上の手順で同じ名前を持つ静的変数を宣言することができます。 これを行う場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラは、このような各変数は別々 の要素を考慮します。 これらの変数のいずれかの初期化では、他の値は影響しません。 同じには、プロシージャのオーバー ロードのセットを定義およびオーバー ロードごとに同じ名前を持つ静的変数を宣言する場合が適用されます。  
  
## <a name="containing-elements-for-static-variables"></a>静的変数のコンテナー要素  
 つまり、そのクラスのプロシージャの中、クラス内で静的ローカル変数を宣言できます。 ただし、構造体のメンバー、またはその構造内のプロシージャのローカル変数として、構造内で静的ローカル変数を宣言できません。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例で変数が宣言、[静的](../../../../visual-basic/language-reference/modifiers/static.md)キーワードです。 (必要としないこと、`Dim`キーワードと、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)など、修飾子を使用して`Static`)。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrKeywords&#13;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>コメント  
 上記の例では、変数`applesSold`手順の後に存在し続けます`runningTotal`呼び出し元のコードを返します。 次回`runningTotal`が呼び出されると、`applesSold`以前の計算値を保持します。  
  
 場合`applesSold`を使用せずに宣言されていた`Static`への呼び出しによる、以前の累積値を保持されませんが`runningTotal`です。 次回`runningTotal`、呼び出された`applesSold`は再作成され、0 に初期化と`runningTotal`あればだけ返さ呼び出されたのと同じ値です。  
  
### <a name="compiling-the-code"></a>コードのコンパイル  
 宣言の一部として静的ローカル変数の値を初期化することができます。 配列を宣言する場合`Static`、そのランク (次元数)、各次元の長さと個々 の要素の値に初期化することができます。  
  
### <a name="security"></a>セキュリティ  
 前の例では、宣言することで有効期間は同じを生成できます`applesSold`モジュール レベルです。 こうすると、変数のスコープを変更した場合は、ただし、プロシージャ不要になったに排他的にアクセスします。 他のプロシージャにアクセスできなかったため`applesSold`とその値を変更、集計の途中の信頼性が低いことがおよび、コードを保守が困難でした。 します。  
  
## <a name="see-also"></a>関連項目  
 [共有](../../../../visual-basic/language-reference/modifiers/shared.md)   
 [何もない](../../../../visual-basic/language-reference/nothing.md)   
 [宣言された要素名](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)
