---
title: Visual Basic における有効期間
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: d32639f1c392d53a7e9f6258440b6c0925d27a5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654230"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic における有効期間
*有効期間*宣言された要素は、期間その中に、使用可能です。 変数は、有効期間がある唯一の要素です。 この目的のため、コンパイラは、プロシージャのパラメーターを処理し、関数は変数の特殊なケースとして返します。 変数の有効期間は、値を保持できる時間の期間を表します。 その有効期間全体でその値を変更することができますが、いくつかの値が常に格納します。  
  
## <a name="different-lifetimes"></a>別の有効期間  
 A*メンバー変数*(プロシージャの外側のモジュール レベルで宣言) が宣言された要素と同じ有効期間は、通常がします。 クラスまたは構造体で宣言されている非共有変数は、クラスまたは構造体が宣言されているのインスタンスごとに個別のコピーとして存在します。 このような各変数では、そのインスタンスと同じ有効期間を持っています。 ただし、`Shared`変数は有効期間は 1 つだけで終了する存続時間全体では、アプリケーションが実行されています。  
  
 A*ローカル変数*(プロシージャ内で宣言) が宣言されているプロシージャの実行中にのみ存在します。 関数の戻り値とそのプロシージャのパラメーターにも当てはまります。 ただし、そのプロシージャがその他のプロシージャを呼び出した場合は、呼び出されたプロシージャが実行中にローカル変数の値は保持します。  
  
## <a name="beginning-of-lifetime"></a>有効期間の開始  
 コントロールが宣言されているプロシージャが入ったときに、ローカル変数の有効期間が開始します。 プロシージャが開始されるとすぐには、すべてのローカル変数をそのデータ型の既定値に初期化を実行しています。 プロシージャが検出した場合、`Dim`初期値を指定するステートメントでは、そのローカル変数に設定これらの値をコードが、それらを他の値を既に割り当てられている場合でもです。  
  
 構造体変数の各メンバーは個別の変数の場合と同様に初期化されます。 同様に、配列変数の各要素は、個別に初期化されます。  
  
 プロシージャ内のブロック内で宣言された変数 (など、`For`ループ)、プロシージャへのエントリに初期化されます。 これらの初期化は、コードには、ブロックが実行されるかどうかよりも反映されます。  
  
## <a name="end-of-lifetime"></a>有効期間の終了  
 プロシージャが終了すると、そのローカル変数の値は保持されませんし、Visual Basic が自らのメモリを解放します。 次回、プロシージャを呼び出すすべてのローカル変数は新しく作成、再初期化します。  
  
 クラスまたは構造体のインスタンスが終了すると、非共有変数には、自らのメモリおよびその値が失われます。 クラスまたは構造体の新しいインスタンスごとでは、作成し、非共有変数を再初期化します。 ただし、`Shared`変数は、アプリケーションの実行が停止されるまで保持されます。  
  
## <a name="extension-of-lifetime"></a>有効期間の延長  
 ローカル変数を宣言する場合、`Static`キーワード、その有効期間は、プロシージャの実行時間より長い。 次の表は、プロシージャの宣言が時間を決定する方法、`Static`変数が存在します。  
  
|プロシージャの場所との共有|静的変数の有効期間を開始します。|静的変数の有効期間の終了|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|(既定では共有) モジュールで|最初に、プロシージャを呼び出す|アプリケーションの実行が終了|  
|クラスでは、 `Shared` (手順は、インスタンス メンバーではありません)|最初に特定のインスタンス、または、クラスまたは構造体名そのものでプロシージャが呼び出されます|アプリケーションの実行が終了|  
|クラスのインスタンスでない`Shared`(プロシージャではインスタンス メンバー)|初めてプロシージャは特定のインスタンスで呼び出されます。|ガベージ コレクション (GC) のインスタンスを解放する場合|  
  
## <a name="static-variables-of-the-same-name"></a>同じ名前の静的変数  
 1 つ以上の手順で同じ名前を持つ静的変数を宣言することができます。 これを行う場合、Visual Basic コンパイラは、このような各変数は別々 の要素を検討します。 これらの変数のいずれかの初期化では、他の値は影響しません。 一連のオーバー ロードを持つプロシージャを定義および各オーバー ロード内の同じ名前を持つ静的変数を宣言する場合にも適用されます。  
  
## <a name="containing-elements-for-static-variables"></a>静的変数のコンテナー要素  
 つまり、そのクラスのプロシージャの中をクラス内で静的ローカル変数を宣言できます。 ただし、構造体のメンバー、またはその構造内のプロシージャのローカル変数として、構造体の内部静的ローカル変数を宣言することはできません。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例の変数の宣言、[静的](../../../../visual-basic/language-reference/modifiers/static.md)キーワード。 (必要としないことに注意してください、`Dim`キーワードと、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)などの修飾子を使用して`Static`)。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>コメント  
 上記の例では、変数`applesSold`、手順の後に存在し続けます`runningTotal`呼び出し元のコードを返します。 次回`runningTotal`が呼び出されると、`applesSold`以前の計算値を保持します。  
  
 場合`applesSold`を使用せずに宣言されている`Static`への呼び出しでは以前の累積値を保持されないは`runningTotal`します。 次回`runningTotal`、呼び出された`applesSold`は再作成され、0 に初期化し、`runningTotal`は単に値が返される、同じ呼び出されました。  
  
### <a name="compiling-the-code"></a>コードのコンパイル  
 宣言の一部として静的ローカル変数の値を初期化することができます。 配列を宣言する場合`Static`、そのランク (次元数)、各次元の長さと、個々 の要素の値に初期化することができます。  
  
### <a name="security"></a>セキュリティ  
 前の例では、宣言することによって有効期間は同じを生成できる`applesSold`モジュール レベルでします。 こうすると、変数のスコープを変更した場合ただし、プロシージャでに排他的にアクセスが必要なくなりましたがあります。 他のプロシージャにアクセスできなかったため`applesSold`とその値を変更、累計が信頼性が高くない可能性があります、コードを維持するためにより困難になることです。  
  
## <a name="see-also"></a>関連項目  
 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)
