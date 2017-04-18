---
title: "Visual Basic での IEnumerable を実装する |Microsoft ドキュメント"
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
- control flow [Visual Basic]
- enumerable interfaces
- loop structures, optimizing performance
- control flow
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
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
ms.openlocfilehash: 68c37c46cbceb1056d50972cdc58ddb7c7577447
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>チュートリアル: Visual Basic での IEnumerable(Of T) の実装
<xref:System.Collections.Generic.IEnumerable%601>インターフェイスは、一度に&1; つの項目の値のシーケンスを返すことができるクラスによって実装されます</xref:System.Collections.Generic.IEnumerable%601>。 データの完全なセットを使用してメモリに読み込みする必要はありません、一度に&1; つの項目は、データを返すことの利点です。 のみ、データから&1; つの項目を読み込むための十分なメモリを使用する必要があるとします。 実装するクラス、`IEnumerable(T)`インターフェイスを使用するで`For Each`ループまたは LINQ クエリ。  
  
 たとえば、大きなテキスト ファイルを読み取る必要があり、特定の検索条件に一致するファイルの各行を返すアプリケーションがあるとします。 アプリケーションでは、LINQ クエリを使用して、指定した条件に一致するファイルから行を返します。 ファイルの内容を照会するには、LINQ クエリを使用して、アプリケーションが、配列またはコレクションに、ファイルの内容を読み込む可能性があります。 ただし、配列またはコレクションにファイル全体を読み込むには、必要なよりはるかに多くのメモリが消費します。 LINQ クエリは、検索条件に一致する値のみを返す、列挙可能なクラスを使用して、ファイルの内容を代わりにクエリでした。 いくつかのみを返すクエリをはるかに少ないメモリを消費し一致する値。  
  
 実装するクラスを作成する、<xref:System.Collections.Generic.IEnumerable%601>列挙可能なデータとしてソース データを公開するインターフェイス</xref:System.Collections.Generic.IEnumerable%601>。 実装するためのクラス、`IEnumerable(T)`インターフェイスを実装する別のクラスが必要になります、<xref:System.Collections.Generic.IEnumerator%601>ソース データを反復処理するインターフェイス</xref:System.Collections.Generic.IEnumerator%601>。 これら&2; つのクラスを使用すると、順番には、特定の種類のデータ項目を返すことができます。  
  
 このチュートリアルを実装するクラスを作成する、`IEnumerable(Of String)`インターフェイスおよび実装するクラス、`IEnumerator(Of String)`を一度にテキスト ファイルの&1; つの行を読み取るインターフェイス。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-enumerable-class"></a>列挙可能なクラスを作成します。  
  
|クラスの列挙可能なプロジェクトを作成するには|  
|---|  
|1.[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。<br />2.**新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。 選択**クラス ライブラリ**で、**テンプレート**ウィンドウです。 **名**ボックスに、入力`StreamReaderEnumerable`、 をクリックし、 **OK**します。 新しいプロジェクトが表示されます。<br />3.**ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**します。 ファイルを`StreamReaderEnumerable.vb`ENTER キーを押します。 ファイルの名前変更の名前も変更は、クラスに`StreamReaderEnumerable`します。 このクラスは実装、`IEnumerable(Of String)`インターフェイスです。<br />4.StreamReaderEnumerable プロジェクトを右クリックし、順にポイント**追加**、クリックして**新しい項目の**です。 選択、**クラス**テンプレートです。 **名**ボックスに、入力`StreamReaderEnumerator.vb` をクリック**OK**します。|  
  
 このプロジェクトの最初のクラスは列挙可能なクラスであり、実装、`IEnumerable(Of String)`インターフェイスです。 このジェネリック インターフェイスを実装して、<xref:System.Collections.IEnumerable>インターフェイスととして型指定された値をこのクラスのコンシューマーがアクセスできることを保証`String`</xref:System.Collections.IEnumerable>。  
  
|IEnumerable を実装するコードを追加するには|  
|---|  
|1.StreamReaderEnumerable.vb ファイルを開きます。<br />2.後の行に`Public Class StreamReaderEnumerable`ENTER キーを押すし、次を入力します。<br />     [!code-vb[VbVbalrIteratorWalkthrough&#1;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動的に入力が必要とするメンバーを持つクラス、`IEnumerable(Of String)`インターフェイスです。<br />3.この列挙可能なクラスに、一度にテキスト ファイルの&1; つの行から行を読み取ります。 ファイル パスを入力パラメーターとして受け取り、パブリック コンス トラクターを公開するクラスに次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough&#2;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.実装、<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>のメソッド、`IEnumerable(Of String)`インターフェイスがの新しいインスタンスを返す、`StreamReaderEnumerator`クラス</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 実装、`GetEnumerator`のメソッド、`IEnumerable`インターフェイスが可能である`Private`のメンバーだけを公開する必要があるため、`IEnumerable(Of String)`インターフェイスです。 コードに置き換えますを[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に対して生成された、`GetEnumerator`メソッドを次のコードでします。<br />     [!code-vb[VbVbalrIteratorWalkthrough&#3;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|IEnumerator を実装するコードを追加するには|  
|---|  
|1.StreamReaderEnumerator.vb ファイルを開きます。<br />2.後の行に`Public Class StreamReaderEnumerator`ENTER キーを押すし、次を入力します。<br />     [!code-vb[VbVbalrIteratorWalkthrough&4;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動的に入力が必要とするメンバーを持つクラス、`IEnumerator(Of String)`インターフェイスです。<br />3.列挙子クラスは、テキスト ファイルを開きし、ファイルをファイルから行を読み取る I/O を実行します。 クラス ファイルのパスを入力パラメーターとして受け取り、パブリック コンス トラクターを公開し、テキスト ファイルを読み取り用に次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough&#5;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.`Current`両方のプロパティ、`IEnumerator(Of String)`と`IEnumerator`インターフェイスでは、テキスト ファイルから現在の項目を返す、`String`です。 実装、`Current`のプロパティ、`IEnumerator`インターフェイスが可能である`Private`のメンバーだけを公開する必要があるため、`IEnumerator(Of String)`インターフェイスです。 コードに置き換えますを[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に対して生成された、`Current`プロパティを次のコードです。<br />     [!code-vb[VbVbalrIteratorWalkthrough&6;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.`MoveNext`のメソッド、`IEnumerator`インターフェイスは、テキスト ファイルに次の項目に移動し、によって返される値を更新して、`Current`プロパティです。 読み取るには、項目がある場合、`MoveNext`メソッドが返す`False`以外の場合、`MoveNext`メソッドを返します。`True`します。 `MoveNext` メソッドに次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough&#7;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.`Reset`のメソッド、`IEnumerator`インターフェイスがテキスト ファイルの先頭を指す反復子に指示し、現在のアイテムの値をクリアします。 `Reset` メソッドに次のコードを追加します。<br />     [!code-vb[VbVbalrIteratorWalkthrough&#8;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.`Dispose`のメソッド、`IEnumerator`インターフェイスで、反復子が破棄される前に、すべてのアンマネージ リソースが解放されることが保証されます。 使用されるファイル ハンドル、`StreamReader`オブジェクトは、アンマネージ リソースであり、反復子インスタンスが破棄される前に閉じる必要があります。 コードに置き換えますを[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に対して生成された、`Dispose`メソッドを次のコードです。<br />     [!code-vb[VbVbalrIteratorWalkthrough&#9;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>サンプルの反復子を使用  
 列挙可能なクラスを使用するには制御構造を実装するオブジェクトを必要とすると、コードで`IEnumerable`など、`For Next`ループまたは LINQ クエリ。 例を次に、 `StreamReaderEnumerable` LINQ クエリでします。  
  
 [!code-vb[VbVbalrIteratorWalkthrough&#10;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)

