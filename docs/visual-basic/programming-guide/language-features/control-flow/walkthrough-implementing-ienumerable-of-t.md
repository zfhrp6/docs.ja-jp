---
title: "Visual Basic で IEnumerable を実装します。"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45b4008f0bf3ae0f303aa029e7bff5b82ab6f259
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>チュートリアル: Visual Basic での IEnumerable(Of T) の実装
<xref:System.Collections.Generic.IEnumerable%601>インターフェイスは、一度に 1 つの項目の値のシーケンスを返すことができるクラスによって実装されます。 データを操作するためのメモリにデータの完全なセットをロードする必要はありませんは、一度に 1 つの項目を返すことの利点です。 のみをデータから 1 つの項目を読み込むための十分なメモリを使用する必要があります。 実装するクラス、`IEnumerable(T)`インターフェイスで使用できる`For Each`ループまたは LINQ クエリ。  
  
 たとえば、大きなテキスト ファイルを読み取りし、特定の検索条件に一致するファイルから各の行を返す必要がありますをアプリケーションがあるとします。 アプリケーションでは、LINQ クエリを使用して、指定した条件に一致するファイルから行を返します。 ファイルの内容を照会するには、LINQ クエリを使用して、アプリケーションが、配列またはコレクションに、ファイルの内容を読み込む可能性があります。 ただし、配列またはコレクションへのファイル全体の読み込みには、必要なよりはるかに多くのメモリが消費します。 LINQ クエリは、検索条件に一致する値のみを返す、列挙可能なクラスを使用して、ファイルの内容を代わりにクエリでした。 一部のみを返すクエリを一致する値ははるかに少ないメモリを消費します。  
  
 実装するクラスを作成することができます、<xref:System.Collections.Generic.IEnumerable%601>列挙可能なデータとしてソース データを公開するインターフェイスです。 実装するためのクラス、`IEnumerable(T)`インターフェイスを実装する別のクラスが必要になります、<xref:System.Collections.Generic.IEnumerator%601>ソース データを反復処理するインターフェイスです。 これら 2 つのクラスを使用すると、順番に、特定の種類のデータ項目を返すことができます。  
  
 このチュートリアルを実装するクラスを作成する、`IEnumerable(Of String)`インターフェイスを実装するクラス、`IEnumerator(Of String)`を一度にテキスト ファイルの 1 つの行を読み取るインターフェイス。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>列挙可能なクラスを作成します。  
  
|クラスの列挙可能なプロジェクトを作成するには|  
|---|  
|1.[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で、**[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。<br />2.**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。 **[名前]** ボックスに `StreamReaderEnumerable` と入力して、**[OK]** をクリックします。 新しいプロジェクトが表示されます。<br />3.**ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**です。 ファイルの名前を `StreamReaderEnumerable.vb` に変更し、Enter キーを押します。 ファイルの名前を変更すると、クラスの名前も `StreamReaderEnumerable` に変更されます。 このクラスが `IEnumerable(Of String)` インターフェイスを実装します。<br />4.StreamReaderEnumerable プロジェクトを右クリックし、**追加**、クリックして**新しい項目の**します。 選択、**クラス**テンプレート。 **名前**ボックスに、入力`StreamReaderEnumerator.vb` をクリック**OK**です。|  
  
 このプロジェクト内の最初のクラスは、列挙可能なクラスであり、実装、`IEnumerable(Of String)`インターフェイスです。 このジェネリック インターフェイスを実装して、<xref:System.Collections.IEnumerable>インターフェイスととして型指定された値をこのクラスのコンシューマーがアクセスできることの保証`String`です。  
  
|IEnumerable を実装するコードを追加するには|  
|---|  
|1.StreamReaderEnumerable.vb ファイルを開きます。<br />2.後の行に`Public Class StreamReaderEnumerable`次を入力して、ENTER キーを押します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]必要なメンバーを持つクラスを自動的に入力、`IEnumerable(Of String)`インターフェイスです。<br />3.この列挙可能なクラスに、一度にテキスト ファイルの 1 つの行から行を読み取ります。 ファイルのパスを入力パラメーターとして取得するパブリック コンス トラクターを公開するクラスに次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.実装、<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>のメソッド、`IEnumerable(Of String)`インターフェイスはの新しいインスタンスを返します、`StreamReaderEnumerator`クラスです。 実装、`GetEnumerator`のメソッド、`IEnumerable`インターフェイスにできる`Private`のメンバーのみを公開する必要があるため、`IEnumerable(Of String)`インターフェイスです。 コードに置き換えますを[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]に対して生成された、`GetEnumerator`次のコードを持つメソッドです。<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|IEnumerator を実装するコードを追加するには|  
|---|  
|1.StreamReaderEnumerator.vb ファイルを開きます。<br />2.後の行に`Public Class StreamReaderEnumerator`次を入力して、ENTER キーを押します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]必要なメンバーを持つクラスを自動的に入力、`IEnumerator(Of String)`インターフェイスです。<br />3.列挙子クラスは、テキスト ファイルを開き、ファイルをファイルから行を読み取る I/O を実行します。 クラスはファイル パスを入力パラメーターとして受け取るパブリック コンス トラクターを公開し、テキスト読み取り用にファイルを開くには、次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.`Current`両方のプロパティ、`IEnumerator(Of String)`と`IEnumerator`インターフェイスとしてテキスト ファイルから現在の項目を返す、`String`です。 実装、`Current`のプロパティ、`IEnumerator`インターフェイスにできる`Private`のメンバーのみを公開する必要があるため、`IEnumerator(Of String)`インターフェイス。 コードに置き換えますを[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]に対して生成された、`Current`次のコードを持つプロパティです。<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.`MoveNext`のメソッド、`IEnumerator`インターフェイスは、テキスト ファイルに次の項目に移動し、によって返される値を更新して、`Current`プロパティです。 読み取るには、これ以上の項目がある場合、`MoveNext`メソッドを返します。`False`以外の場合、`MoveNext`メソッドを返します。`True`です。 `MoveNext` メソッドに次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.`Reset`のメソッド、`IEnumerator`インターフェイスがテキスト ファイルの先頭を指す反復子に指示し、現在の項目の値をクリアします。 `Reset` メソッドに次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.`Dispose`のメソッド、`IEnumerator`インターフェイスは、反復子が破棄される前に、すべてのアンマネージ リソースが離されたことを保証します。 によって使用されるファイル ハンドル、`StreamReader`オブジェクトは、アンマネージ リソースであり、反復子インスタンスが破棄される前に閉じる必要があります。 コードに置き換えますを[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]に対して生成された、`Dispose`メソッドを次のコード。<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>サンプルの反復子を使用します。  
 制御構造を実装するオブジェクトを必要とすると、コードで列挙可能なクラスを使用することができます`IEnumerable`、ように、`For Next`ループまたは LINQ クエリを実行します。 次の例は、 `StreamReaderEnumerable` LINQ クエリにします。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
