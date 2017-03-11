---
title: "SyncLock Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.SyncLock"
  - "SyncLock"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "threading [Visual Basic], locks"
  - "SyncLock statement"
  - "locks, threads"
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# SyncLock Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ステートメント ブロックを実行する前に、そのブロックに対する排他ロックを取得します。  
  
## 構文  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## 指定項目  
 `lockobject`  
 必須。  オブジェクト参照に評価される式です。  
  
 `block`  
 省略可能。  ロックを取得したとき実行されるステートメントのブロックです。  
  
 `End SyncLock`  
 `SyncLock` ブロックを終了します。  
  
## 解説  
 `SyncLock` ステートメントを使用すると、複数のスレッドがステートメント ブロックを同時に実行するのを回避できます。  `SyncLock` は、ブロックを実行しているスレッドがなくなるまで、各スレッドがそのブロックに入るのを防ぎます。  
  
 ほとんどの場合、`SyncLock` は、複数のスレッドによってデータが同時に更新されないよう保護するために使用されます。  データを操作するステートメントを、途中で割り込まれることなく最後まで実行する必要がある場合は、ステートメントを `SyncLock` ブロックの内部に記述してください。  
  
 排他ロックに保護されるステートメント ブロックは、*クリティカル セクション*と呼ばれることもあります。  
  
## 規則  
  
-   分岐。  `SyncLock` ブロックの外部からブロックに分岐することはできません。  
  
-   ロック オブジェクトの値。  `lockobject` の値を `Nothing` にすることはできません。  ロック オブジェクトは、`SyncLock` ステートメントで使用する前に作成する必要があります。  
  
     `SyncLock` ブロックの実行中に、`lockobject` の値を変更しないでください。  排他ロックでは、ロック オブジェクトは変更されないでいることが必要です。  
  
-   `SyncLock` ブロックで [待機します。](../../../visual-basic/language-reference/operators/await-operator.md) の演算子は使用できません。  
  
## \[動作\]  
  
-   しくみ。  スレッドは `SyncLock` ステートメントに到達すると、`lockobject` 式を評価して、式によって返されたオブジェクトの排他ロックを取得するまで実行を中断します。  別のスレッドが `SyncLock` ステートメントに到達しても、そのスレッドは最初のスレッドが `End SyncLock` ステートメントを実行するまでロックを取得しません。  
  
-   データの保護。  `lockobject` が `Shared` であれば、排他ロックは他のスレッドが `SyncLock` ブロックを実行している間は、クラスのどのインスタンス内のスレッドにも `SyncLock` ブロックを実行させません。  これにより、すべてのインスタンスで共有されているデータを保護できます。  
  
     `lockobject` が \(`Shared` 変数ではなく\) インスタンス変数であれば、排他ロックは現在のインスタンスで動作しているスレッドが、同じインスタンス内の別のスレッドと同時に `SyncLock` ブロックを実行するのを防ぎます。  これにより、個々のインスタンスで保持されるデータを保護できます。  
  
-   取得と解放。  `SyncLock` ブロックは `Try...Finally` 構造に動作が似ており、`Try` ブロックで `lockobject` に対する排他ロックを取得し、`Finally` ブロックでロックを解放するように動作します。  このため、`SyncLock` ブロックは、ブロックがどのように終了された場合でも、ロックを必ず解放します。  これは、未処理の例外の場合にも該当します。  
  
-   Framework の呼び出し。  `SyncLock` ブロックは、<xref:System.Threading> 名前空間にある `Monitor` クラスの `Enter` メソッドと `Exit` メソッドを呼び出して、排他ロックを取得および解放します。  
  
## プログラミング手法  
 `lockobject` 式は、必ずクラスに排他的に属するオブジェクトに評価される必要があります。  現在のインスタンスに属するデータを保護する場合は `Private` オブジェクト変数を宣言し、すべてのインスタンスに共通のデータを保護するには、`Private Shared` オブジェクト変数を宣言します。  
  
 キーワード `Me` を使用して、ロック オブジェクトをインスタンス データから利用できるようにしないでください。  自分のクラスの外部にあるコードが、自分のクラスのインスタンスを参照する場合、`SyncLock` ブロックのロック オブジェクトが自分のロック オブジェクトとはまったく異なり、別々のデータを保護しているにもかかわらず、外部のコードがその参照を使用する可能性があります。  このとき、自分のクラスと外部のクラスは互いにブロックし合って、関係のない `SyncLock` ブロックを実行させないようにします。  同様に、文字列をロックする場合も問題が起きる可能性があります。プロセス内で同じ文字列を使用している他のすべてのコードが、同じロックを共有することになるからです。  
  
 また、`Me.GetType` メソッドを使用して、ロック オブジェクトを共有データから利用できるようにしないでください。  なぜなら、`GetType` は特定のクラス名に対して、必ず同じ `Type` オブジェクトを返すためです。  外部のコードが自分のクラスで `GetType` を呼び出し、自分が使用しているのと同じロック オブジェクトを取得する可能性があります。  この結果、2 つのクラスが互いにブロックし合って、`SyncLock` ブロックを実行させなくなります。  
  
## 例  
  
### 説明  
 メッセージの簡単なリストを保持するクラスは、次の例のようになります。  このクラスはメッセージを配列に格納し、その配列で最後に使用された要素を変数に格納します。  `addAnotherMessage` プロシージャは最後の要素をインクリメントし、新しいメッセージを格納します。  これら 2 つの処理は `SyncLock` ステートメントと `End SyncLock` ステートメントで保護します。なぜなら、最後の要素がインクリメントされた後、他のスレッドが最後の要素をもう一度インクリメントする前に、新しいメッセージを格納する必要があるからです。  
  
 `simpleMessageList` クラスが 1 つのメッセージ リストをすべてのインスタンスで共有する場合は、`messagesList` 変数と `messagesLast` 変数を `Shared` として宣言します。  この場合、`messagesLock` も `Shared` で宣言して、すべてのインスタンスが単一のロック オブジェクトを使用するようにしてください。  
  
### コード  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/synclock-statement_1.vb)]  
  
### 説明  
 次の例では、スレッドおよび `SyncLock` が使用されています。  `SyncLock` ステートメントが存在する限り、ステートメント ブロックはクリティカル セクションであり、`balance` は負の数にはなりません。  `SyncLock` ステートメントと `End SyncLock` ステートメントをコメント アウトすると、`SyncLock` キーワードを使用しない場合の効果を確認できます。  
  
### コード  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/synclock-statement_2.vb)]  
  
### コメント  
  
## 参照  
 <xref:System.Threading>   
 <xref:System.Threading.Monitor>   
 [スレッドの同期](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)   
 [スレッド](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)