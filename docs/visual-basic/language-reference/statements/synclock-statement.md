---
title: "SyncLock ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c363b41bb7a409c490a6e07d4a1a4f1bb44c1438
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="synclock-statement"></a>SyncLock ステートメント
ブロックを実行する前にステートメント ブロックの排他ロックを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>指定項目  
 `lockobject`  
 必須。 オブジェクト参照に評価される式。  
  
 `block`  
 任意。 ロックが取得されたときに実行されるステートメントのブロックです。  
  
 `End SyncLock`  
 終了、`SyncLock`ブロックします。  
  
## <a name="remarks"></a>コメント  
 `SyncLock`ステートメントが複数のスレッドを実行しない、ステートメント ブロック、同時にことを確認します。 `SyncLock`各スレッドが実行している他のスレッドがなくなるまで、ブロックを入力するを防ぎます。  
  
 最も一般的な使用`SyncLock`から複数のスレッドで同時に更新されているデータを保護することです。 場合は、データを操作するステートメントは、中断することがなく完了に移動する必要があります、その内部配置、`SyncLock`ブロックします。  
  
 排他ロックによって保護されているステートメント ブロックが呼び出される場合があります、*クリティカル セクション*です。  
  
## <a name="rules"></a>ルール  
  
-   分岐します。 内に分岐することはできません、`SyncLock`ブロックの外側からブロックされます。  
  
-   ロック オブジェクト値です。 値`lockobject`することはできません`Nothing`です。 使用する前に、ロック オブジェクトを作成する必要があります、`SyncLock`ステートメントです。  
  
     値を変更することはできません`lockobject`の実行中に、`SyncLock`ブロックします。 このメカニズムでは、ロック オブジェクトが変化が必要です。  
  
-   使用することはできません、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)の演算子、`SyncLock`ブロックします。  
  
## <a name="behavior"></a>動作  
  
-   メカニズムです。 スレッドに達したとき、`SyncLock`ステートメントでは、評価、`lockobject`式、式によって返されるオブジェクトの排他ロックを取得するまで実行を中断します。 別のスレッドに達したとき、`SyncLock`ステートメントでは、これはロックを取得、最初のスレッドが実行されるまで、`End SyncLock`ステートメントです。  
  
-   保護されるデータ。 場合`lockobject`は、`Shared`変数、排他ロック クラスの任意のインスタンス内のスレッドが実行されないように、`SyncLock`他のスレッドを実行している場合にブロックします。 これは、すべてのインスタンス間で共有されているデータを保護します。  
  
     場合`lockobject`インスタンス変数は、(いない`Shared`)、ロックにより、スレッドの実行から現在のインスタンスで実行できなくなります、`SyncLock`で、同じインスタンス内の別のスレッドと同時にブロックします。 これは、個別のインスタンスで保持されているデータを保護します。  
  
-   取得と解放します。 A`SyncLock`ブロックの動作と同様に、`Try...Finally`を構築、`Try`ブロックに排他ロックを取得する`lockobject`と`Finally`ブロックを解放します。 このため、`SyncLock`ブロック、ブロックを終了する方法に関係なく、ロックの解放を保証します。 これは、未処理の例外場合でも当てはまります。  
  
-   フレームワークです。 `SyncLock`ブロックを取得し、呼び出すことによって、排他ロックを解放、`Enter`と`Exit`のメソッド、`Monitor`クラス内で、<xref:System.Threading>名前空間。  
  
## <a name="programming-practices"></a>プログラミング手法  
 `lockobject`式は常をクラスにのみ属しているオブジェクトを評価する必要があります。 宣言する必要があります、`Private`オブジェクト変数を現在のインスタンスに属するデータを保護または`Private Shared`オブジェクト変数をすべてのインスタンスに共通のデータを保護します。  
  
 使用しないで、`Me`オブジェクトのインスタンスのデータのキーワードをロックを指定します。 ロック オブジェクトとしてその参照を使用、クラスの外部のコードに、クラスのインスタンスへの参照がある場合、`SyncLock`ブロック、自分のものとはまったく異なる別のデータを保護します。 この方法で、クラスとその他のクラスでした互いにブロックの実行、関連付けられていない`SyncLock`ブロックします。 同様に、文字列をロックが問題となる、同じ文字列を使用して、プロセス内の他のすべてのコードは、同じロックを共有するためです。  
  
 使用しないでも、`Me.GetType`ロック オブジェクトを提供するメソッドがデータを共有します。 これは、ため`GetType`常に同じを返します`Type`オブジェクトの特定のクラス名。 外部コードを呼び出すことが`GetType`クラスを使用している同じロック オブジェクトを取得します。 これは、結果から互いをブロックして 2 つのクラスとして、`SyncLock`ブロックします。  
  
## <a name="examples"></a>例  
  
### <a name="description"></a>説明  
 次の例では、メッセージの単純なリストを保持するクラスを示します。 配列内のメッセージを保持し、最後は、変数にその配列の要素を使用します。 `addAnotherMessage`プロシージャが最後の要素をインクリメントし、新しいメッセージを格納します。 これら 2 つの操作で保護されている、`SyncLock`と`End SyncLock`ステートメント、他のスレッドでは、最後の要素をもう一度インクリメント前に、新しいメッセージを格納する必要が最後の要素をインクリメントすると後であるためです。  
  
 場合、`simpleMessageList`クラスはすべて、そのインスタンスの変数間のメッセージの 1 つのリストを共有`messagesList`と`messagesLast`として宣言することは`Shared`します。 この場合、変数`messagesLock`すべき`Shared`、すべてのインスタンスによって使用される 1 つのロック オブジェクトがあるようにします。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>説明  
 次の例は、スレッドを使用し、`SyncLock`です。 限り、`SyncLock`ステートメント、ステートメント ブロックは、クリティカル セクションと`balance`ことはありませんが、負の数になります。 コメント アウトすることができます、`SyncLock`と`End SyncLock`が除外の影響を確認するステートメント、`SyncLock`キーワード。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>コメント  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [スレッドの同期](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [スレッド化](../../programming-guide/concepts/threading/index.md)
