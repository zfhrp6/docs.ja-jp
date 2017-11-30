---
title: "方法 : Visual Basic でファイルを作成する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e6785086f8c97f983c6dcd6fd713c01e34e258
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-file-in-visual-basic"></a>方法 : Visual Basic でファイルを作成する
この例では、<xref:System.IO.File> クラスで <xref:System.IO.File.Create%2A> メソッドを使用して、指定したパスに空のテキスト ファイルを作成します。  
  
## <a name="example"></a>例  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 ファイルに書き込むには、`file` 変数を使用します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ファイルが既に存在する場合、それは置き換えられます。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パス名が不適切である場合。 たとえば、不正な文字が含まれている場合や、空白だけの場合などです (<xref:System.ArgumentException>)。  
  
-   パスが読み取り専用の場合 (<xref:System.IO.IOException>)。  
  
-   パス名が `Nothing` の場合 (<xref:System.ArgumentNullException>)。  
  
-   パス名が長すぎる場合 (<xref:System.IO.PathTooLongException>)。  
  
-   パスが無効な場合 (<xref:System.IO.DirectoryNotFoundException>)。  
  
-   パスがコロン ":" のみである場合 (<xref:System.NotSupportedException>)。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 部分信頼環境では、<xref:System.Security.SecurityException> がスローされる場合があります。  
  
 <xref:System.IO.File.Create%2A> メソッドへの呼び出しでは、<xref:System.Security.Permissions.FileIOPermission> が必要です。  
  
 ユーザーがファイルを作成するアクセス許可を持っていない場合、<xref:System.UnauthorizedAccessException> がスローされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [部分信頼コードからライブラリを使用します。](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [コード アクセス セキュリティの基礎](https://msdn.microsoft.com/library/33tceax8)
