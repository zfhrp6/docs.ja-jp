---
title: "方法 : Visual Basic でファイル パスを解析する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 913fe45cf6fc7afdc6e0f31e028bc18808cecf89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>方法 : Visual Basic でファイル パスを解析する
<xref:Microsoft.VisualBasic.FileIO.FileSystem> オブジェクトには、ファイル パスを解析するときに役立つメソッドがいくつか用意されています。  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> メソッドは、2 つのパスを受け取り、適切な書式で結合されたパスを返します。  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> メソッドは、指定されたパスの親の絶対パスを返します。  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> メソッドは、 <xref:System.IO.FileInfo> オブジェクトを返します。このオブジェクトを照会すると、ファイルのプロパティ (名前やパスなど) を確認できます。  
  
 ファイル名の拡張子に基づいてファイルの内容を判断しないでください。 たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。  
  
### <a name="to-determine-a-files-name-and-path"></a>ファイルの名前とパスを確認するには  
  
-   <xref:System.IO.FileInfo.DirectoryName%2A> オブジェクトの <xref:System.IO.FileInfo.Name%2A> および <xref:System.IO.FileInfo> プロパティを使用して、ファイルの名前とパスを確認します。 この例は、名前とパスを確認し、それらを表示します。  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>ファイルの名前とディレクトリを結合して完全パスを作成するには  
  
-   `CombinePath` メソッドを使用し、ディレクトリと名前を指定します。 この例では、前の例で作成した文字列 `folderPath` と `fileName` を受け取って、両者を結合し、結果を表示します。  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [方法: ディレクトリにあるファイルのコレクションを取得する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
