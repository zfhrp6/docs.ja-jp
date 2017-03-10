---
title: "Walkthrough: Creating and Implementing Interfaces (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interfaces, walkthroughs"
  - "interfaces, testing"
  - "interface implementation, walkthrough"
  - "interfaces, creating"
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Walkthrough: Creating and Implementing Interfaces (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

インターフェイスはプロパティ、メソッド、およびイベントの特性を記述しますが、その実装の詳細は構造体やクラスに依存しています。  
  
 このチュートリアルでは、インターフェイスの宣言および実装の方法を説明します。  
  
> [!NOTE]
>  このチュートリアルでは、方法に関する情報をユーザー インターフェイスを作成するありません。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### インターフェイスを定義するには  
  
1.  新しい [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] Windows アプリケーション プロジェクトを開きます。  
  
2.  **\[プロジェクト\]** メニューの **\[標準モジュールの追加\]** をクリックして、新規モジュールをプロジェクトに追加します。  
  
3.  新規モジュールに `Module1.vb` という名前を付け、**\[追加\]** をクリックします。  新規モジュールのコードが表示されます。  
  
4.  `Module` ステートメントと `End Module` ステートメントの間に「`Interface TestInterface`」と入力し、Enter を押して、`TestInterface` という名前のインターフェイスを `Module1` で定義します。  **コード エディター**によって `Interface` キーワードがインデントされ、`End Interface` ステートメントが追加されてコード ブロックが形成されます。  
  
5.  `Interface` ステートメントと `End Interface` ステートメントの間に次のコードを記述して、インターフェイスのプロパティ、メソッド、およびイベントを定義します。  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#98)]  
  
## 実装  
 インターフェイス メンバーを宣言する構文は、クラス メンバーを宣言する構文と異なります。  この違いは、インターフェイスには実装コードを含めることができないという事実を表しています。  
  
#### インターフェイスを実装するには  
  
1.  `Module1` に `ImplementationClass` という名前のクラスを追加します。`End Interface` ステートメントと `End Module` ステートメントの間に次のステートメントを追加し、Enter キーを押します。  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#99)]  
  
     統合開発環境で作業している場合、Enter キー を押すことによって、対応する `End Class` ステートメントが**コード エディター**に追加されます。  
  
2.  次の `Implements` ステートメントを `ImplementationClass` に追加します。これによって、クラスが実装するインターフェイスが指定されます。  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#100)]  
  
     `Implements` ステートメントがクラスまたは構造体の先頭で他の項目と分かれて記述されている場合は、クラスまたは構造体がインターフェイスを実装することを意味します。  
  
     統合開発環境で作業している場合、Enter を押すと**コード エディター**によって `TestInterface` で必要なクラス メンバーが実装され、次の手順は省略できます。  
  
3.  統合開発環境で作業している場合、インターフェイス `MyInterface` のすべてのメンバーを実装する必要があります。  次のコードを `ImplementationClass` に追加して `Event1`、`Method1`、`Prop1` を実装します。  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#101)]  
  
     `Implements` ステートメントは、実装されるインターフェイスとインターフェイスのメンバーの名前を指定します。  
  
4.  プロパティの値を格納したクラスにプライベート フィールドを追加することで、`Prop1` の定義を完了します。  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#102)]  
  
     `pval` の値を、プロパティの get アクセサーから返します。  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#103)]  
  
     `pval` の値を、プロパティの set アクセサーに設定します。  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#104)]  
  
5.  次のコードを追加して、`Method1` の定義を完了します。  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#105)]  
  
#### インターフェイスの実装をテストするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトのスタートアップ フォームを右クリックし、**\[コードの表示\]** をクリックします。  スタートアップ フォームのクラスがエディターに表示されます。  スタートアップ フォームの名前は既定で `Form1` となります。  
  
2.  次の `testInstance` フィールドを `Form1` クラスに追加します。  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#120)]  
  
     `testInstance` を `WithEvents` として宣言することで、`Form1` クラスはそのイベントを処理できるようになります。  
  
3.  `testInstance` によって発生するイベントを処理するために、次のイベント ハンドラーを `Form1` に追加します。  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#106)]  
  
4.  `Test` というサブルーチンを `Form1` クラスに追加して、実装クラスをテストします。  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#107)]  
  
     `Test` プロシージャは、`MyInterface` を実装するクラスのインスタンスを作成し、そのインスタンスを `testInstance` フィールドに代入し、プロパティを設定し、そのインターフェイスを経由してメソッドを実行します。  
  
5.  スタートアップ フォームの `Form1 Load` プロシージャから `Test` プロシージャを呼び出すコードを追加します。  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#108)]  
  
6.  F5 キーを押して `Test` プロシージャを実行します。  "Prop1 was set to 9" というメッセージが表示されます。  \[OK\] をクリックすると、"The X parameter for Method1 is 5" というメッセージが表示されます。  \[OK\] をクリックすると、"The event handler caught the event" というメッセージが表示されます。  
  
## 参照  
 [Implements Statement](../../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)   
 [Interface Statement](../../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md)