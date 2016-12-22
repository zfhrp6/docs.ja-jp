---
title: "Walkthrough: Implementing IEnumerable(Of T) in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "control flow [Visual Basic]"
  - "enumerable interfaces"
  - "loop structures, optimizing performance"
  - "control flow"
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Implementing IEnumerable(Of T) in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

<xref:System.Collections.Generic.IEnumerable%601> インターフェイスは、クラスに実装し、一連の値を一度に 1 項目ずつ返すことができるようにします。  データを一度に 1 項目ずつ返す利点は、データを処理するために、データ全体のセットをメモリに読み込む必要がないことです。  単一の項目をデータから読み込むために必要なメモリしか使用する必要がありません。  `IEnumerable(T)` インターフェイスを実装するクラスは、`For Each` ループまたは LINQ クエリで使用できます。  
  
 例として、大きなテキスト ファイルを読み込み、特定の検索条件と一致する各行をファイルから返すアプリケーションを考えます。  このアプリケーションでは、指定した条件と一致する行をファイルから返すために、LINQ クエリを使用します。  LINQ クエリを使用してファイルの内容を照会するために、アプリケーションはファイルの内容を配列またはコレクションに読み込みます。  しかし、ファイル全体を配列またはコレクションに読み込むと、必要なメモリ量よりはるかに多く消費することになります。  そうする代わりに、LINQ クエリでは、列挙可能なクラスを使用することで、検索条件と一致する値のみを返すようにファイルの内容を照会できます。  何件かの一致する値のみを返すクエリであれば、消費するメモリ量は格段に少なくて済みます。  
  
 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するクラスを作成し、ソース データを列挙可能なデータとして公開できます。  この `IEnumerable(T)` インターフェイスを実装するクラスは、ソース データ全体を反復処理するために、<xref:System.Collections.Generic.IEnumerator%601> インターフェイスを実装する別のクラスを必要とします。  これら 2 つのクラスを使用することで、データ項目を特定の型として順次返すことができます。  
  
 このチュートリアルでは、テキスト ファイルを一度に 1 行ずつ読み取るための、`IEnumerable(Of String)` インターフェイスを実装するクラスと、`IEnumerator(Of String)` インターフェイスを実装するクラスを作成します。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## 列挙可能なクラスの作成  
  
||  
|-|  
|列挙可能なクラス プロジェクトを作成するには|  
|1.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。<br />2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[プロジェクトの種類\]** ペインで、**\[Windows\]** が選択されていることを確認します。  **\[テンプレート\]** ペインで **\[クラス ライブラリ\]** をクリックします。  **\[プロジェクト名\]** ボックスに「`StreamReaderEnumerable`」と入力し、**\[OK\]** をクリックします。  新しいプロジェクトが表示されます。<br />3.  **ソリューション エクスプローラー**で、Class1.vb ファイルを右クリックし、**\[名前の変更\]** をクリックします。  ファイルの名前を `StreamReaderEnumerable.vb` に変更し、Enter キーを押します。  ファイルの名前を変更すると、クラスの名前も `StreamReaderEnumerable` に変更されます。  このクラスは、`IEnumerable(Of String)` インターフェイスを実装します。<br />4.  StreamReaderEnumerable プロジェクト ノードを右クリックし、**\[追加\]** をポイントして、**\[新しい項目\]** をクリックします。  **\[クラス\]** テンプレートを選択します。  **\[プロジェクト名\]** ボックスに「`StreamReaderEnumerator.vb`」と入力し、**\[OK\]** をクリックします。|  
  
 このプロジェクトの最初のクラスは列挙可能なクラスであり、`IEnumerable(Of String)` インターフェイスを実装します。  このジェネリック インターフェイスが <xref:System.Collections.IEnumerable> インターフェイスを実装し、このクラスのコンシューマーが `String` 型に設定された値にアクセスできることを保証します。  
  
||  
|-|  
|IEnumerable を実装するコードを追加するには|  
|1.  StreamReaderEnumerable.vb ファイルを開きます。<br />2.  `Public Class StreamReaderEnumerable` の後の行に次のように入力し、Enter キーを押します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] により、クラスに `IEnumerable(Of String)` インターフェイスで必要なメンバーが自動的に設定されます。<br />3.  この列挙可能なクラスは、テキスト ファイルから一度に 1 行ずつ読み取ります。  ファイルのパスを入力パラメーターとして取得するパブリック コンストラクターを公開するため、次のコードをクラスに追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  `IEnumerable(Of String)` インターフェイスの <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドの実装は、`StreamReaderEnumerator` クラスの新しいインスタンスを返します。  `IEnumerable` インターフェイスの `GetEnumerator` メソッドの実装は、`IEnumerable(Of String)` インターフェイスのメンバーのみを公開すればよいため、`Private` にすることができます。  `GetEnumerator` メソッドに対して [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で生成されたコードを、次のコードに置き換えます。<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
||  
|-|  
|IEnumerator を実装するコードを追加するには|  
|1.  StreamReaderEnumerator.vb ファイルを開きます。<br />2.  `Public Class StreamReaderEnumerator` の後の行に次のように入力し、Enter キーを押します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] により、クラスに `IEnumerator(Of String)` インターフェイスで必要なメンバーが自動的に設定されます。<br />3.  列挙子クラスがテキスト ファイルを開き、ファイル I\/O を実行してファイルの行を読み取ります。  ファイルのパスを入力パラメーターとして取得し、読み取りのためにテキスト ファイルを開くパブリック コンストラクターを公開するため、次のコードをクラスに追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  `IEnumerator(Of String)` インターフェイスおよび `IEnumerator` インターフェイスの両方の `Current` プロパティは、テキスト ファイルから現在の項目を `String` として返します。  `IEnumerator` インターフェイスの `Current` プロパティの実装は、`IEnumerator(Of String)` インターフェイスのメンバーのみを公開すればよいため、`Private` にすることができます。  `Current` プロパティに対して [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で生成されたコードを、次のコードに置き換えます。<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  `IEnumerator` インターフェイスの `MoveNext` メソッドはテキスト ファイル内の次の項目に移動し、`Current` プロパティで返される値を更新します。  読み取る項目がなくなった場合、`MoveNext` メソッドは `False` を返し、それ以外の場合、`MoveNext` メソッドは `True` を返します。  `MoveNext` メソッドに次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  `IEnumerator` インターフェイスの `Reset` メソッドは、テキスト ファイルの最初をポイントするように反復子を移動し、現在の項目の値を消去します。  `Reset` メソッドに次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  `IEnumerator` インターフェイスの `Dispose` メソッドは、反復子が破棄される前に、すべてのアンマネージ リソースがリリースされることを保証します。  `StreamReader` オブジェクトで使用されるファイル ハンドルはアンマネージ リソースであり、反復子インスタンスが破棄される前に閉じる必要があります。  `Dispose` メソッドに対して [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で生成されたコードを、次のコードに置き換えます。<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## サンプル反復子の使用  
 列挙可能なクラスは、`For Next` ループや LINQ クエリなどの `IEnumerable` を実装するオブジェクトを必要とするコントロール構造体と一緒にコード内で使用することができます。  次の例は、LINQ クエリ内の `StreamReaderEnumerable` を示しています。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)