---
title: "方法: My Documents ディレクトリのファイルにテキストを書き込む (Visual Basic) | Microsoft Docs"
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
- files, writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files, in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: 19
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 848f7c3eac56f85d2af4c613645d54b70061d072
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>方法: My Documents ディレクトリのファイルにテキストを書き込む (Visual Basic)
`My.Computer.FileSystem.SpecialDirectories` オブジェクトを使うと、**[MyDocuments]** ディレクトリなどの特別なディレクトリにアクセスできます。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>[MyDocuments] ディレクトリに新しいテキスト ファイルを書き込むには  
  
1.  `My.Computer.FileSystem.SpecialDirectories.MyDocuments` プロパティを使ってパスを指定します。  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  `WriteAllText` メソッドを使って、指定したファイルにテキストを書き込みます。  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a>例  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 `test.txt` を、実際に書き込むファイルの名前に置き換えます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 このコードでは、ファイルにテキストを書き込むときに発生する可能性のあるすべての例外が再スローされます。 ユーザーの選択肢を有効なファイル名に制限する [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) コンポーネントや [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) コンポーネントなどの Windows フォーム コントロールを使うことで、例外が発生する可能性を減らすことができます。 ただし、これらのコントロールを使ったからといって例外がまったくなくなるわけではありません。 ユーザーがファイルを選んだ時点から、コードが実行される時点までの間に、ファイル システムが変化する可能性があります。 ですから、ファイルを操作するときはほとんど常に、例外処理が必要になります。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 部分的に信頼されたコンテキストで実行している場合、コードは、特権がないために例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](https://msdn.microsoft.com/library/33tceax8)」をご覧ください。  
  
 この例では、新しいファイルを作成します。 アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する Create アクセス許可が必要です。 アクセス許可は、アクセス制御リストを使って設定します。 ファイルが既に存在する場合、アプリケーションに必要なのは低い権限の Write アクセス許可だけです。 可能な場合は、フォルダーに対する Create アクセス許可を付与するのではなく、展開の間にファイルを作成しておき、1 つのファイルの Read アクセス許可を付与するだけの方が安全です。 また、ルート フォルダーや **[Program Files]** フォルダーにデータを書き込むより、ユーザー フォルダーに書き込む方が安全です。 詳しくは、「[アクセス制御リスト (ACL: Access Control List) 技術の概要](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.Path.Combine%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
