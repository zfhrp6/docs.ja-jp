---
title: "LINQ とファイル ディレクトリ (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5536ae95b42cdaddda2c4cae97a114681e94b0ab
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ とファイル ディレクトリ (Visual Basic)
多くのファイル システム操作はクエリでは基本的にはであり、LINQ アプローチによく適しているためです。  
  
 このセクションでクエリが非破壊的なことに注意してください。 元のファイルまたはフォルダーの内容を変更するのには使用されません。 クエリが副次的な影響を引き起こさないことルールに従います。 一般に、ソース データを変更するコード (を実行するなどのクエリを作成/更新/delete 演算子) おく必要がある別のデータを単にクエリを実行するコードです。  
  
 このセクションでは、以下のトピックについて説明します。  
  
 [方法: 指定された属性または名前 (Visual Basic) のファイルをクエリ](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 1 つ以上のプロパティを確認するには、ファイルを検索する方法を示しています、<xref:System.IO.FileInfo>オブジェクト</xref:System.IO.FileInfo>。  
  
 [方法: 拡張機能 (LINQ) (Visual Basic) でファイルをグループ化](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 グループを返す方法を示しています<xref:System.IO.FileInfo>オブジェクトに基づいて、ファイル名拡張子</xref:System.IO.FileInfo>。  
  
 [方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数を問い合わせる](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 指定したディレクトリ ツリー内のすべてのファイルの合計バイト数を返す方法を示します。  
  
 [方法:&2; つのフォルダー (LINQ) (Visual Basic) の内容を比較](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 2 つの指定したフォルダーに存在するすべてのファイルとファイルをすべて&1; つのフォルダーに存在するを返す方法を示します。  
  
 [方法: ファイルまたはディレクトリ ツリー (LINQ) (Visual Basic) 内のファイル サイズの大きい照会](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 ディレクトリ ツリーで、最大値または最小のファイルまたはファイルの指定した数を返す方法を示します。  
  
 [方法: ディレクトリ ツリー (LINQ) (Visual Basic) で重複するファイルのクエリ](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 指定したディレクトリ ツリー内で複数の場所で発生するすべてのファイル名のグループ化する方法を示します。 カスタムの比較演算子に基づいてさらに複雑な比較を実行する方法も示します。  
  
 [方法: クエリ (LINQ) (Visual Basic) のフォルダー内のファイルの内容](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 ツリー内のフォルダーを反復処理を各ファイルを開き、ファイルの内容を照会する方法を示します。  
  
## <a name="comments"></a>コメント  
 何らかの複雑性は正確にファイル システムの内容を表すし、例外が適切に処理するデータ ソースの作成に必要です。 このセクションの例のスナップショット コレクションの作成<xref:System.IO.FileInfo>指定したルート フォルダーの下のすべてのファイルとそのすべてのサブフォルダーを表すオブジェクト</xref:System.IO.FileInfo>。 それぞれの実際の状態<xref:System.IO.FileInfo>を開始し、クエリの実行を終了するときまでの間に変更することがあります</xref:System.IO.FileInfo>。 一覧を作成するなど、<xref:System.IO.FileInfo>データ ソースとして使用するオブジェクト</xref:System.IO.FileInfo>。 アクセスしようとする場合、`Length`クエリでは、プロパティ、<xref:System.IO.FileInfo>の値を更新するファイル システムにアクセスしようとして、オブジェクト`Length`</xref:System.IO.FileInfo>。 ファイルが存在しない場合、表示、 <xref:System.IO.FileNotFoundException>、クエリでもないクエリを実行するファイル システム直接</xref:System.IO.FileNotFoundException>。 このセクションの一部のクエリでは、特定の場合にこれらの特定の例外を使用する別のメソッドを使用します。 <xref:System.IO.FileSystemWatcher>。</xref:System.IO.FileSystemWatcher>を使用して動的に更新されるデータ ソースを保持することもできます。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
