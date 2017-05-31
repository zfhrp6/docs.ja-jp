---
title: "ファイル エンコーディング (Visual Basic) | Microsoft Docs"
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
- character encodings
- files, encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: 8
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d59312951429780990e9cc048e3ad0671b81d8ae
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="file-encodings-visual-basic"></a>ファイル エンコーディング (Visual Basic)
ファイル エンコーディングは、文字エンコーディングとも呼ばれ、テキストを処理するときの文字の表現方法を指定します。 言語で処理できる (または処理できない) 文字という観点から、あるエンコードが他のエンコーディングよりも望ましいということがありますが、一般的には Unicode が好まれます。  
  
 ファイルに対する読み取りと書き込みでは、ファイル エンコーディングが適切に一致しないと、例外が発生したり、不正な結果となる場合があります。  
  
## <a name="types-of-encodings"></a>エンコーディングの種類  
 ファイルを扱うときには、Unicode は最適なエンコーディングです。 Unicode は、世界共通の文字エンコーディング規則で、技術的な記号や出版で使用される特殊文字などを含む、現在のコンピューティングで使用されるすべての文字を、16 ビットのコード値で表します。  
  
 これまでの文字エンコーディング規則は、Windows ANSI 文字セットなどの従来からある文字セットで構成されており、8 ビットのコード値や 8 ビット値の組み合わせを使用して、特定の言語や地域で使用する文字を表していました。  
  
## <a name="encoding-class"></a>Encoding クラス  
 <xref:System.Text.Encoding> クラスは文字エンコーディングを表します。 次の表は、利用可能なエンコーディングの型の一覧とそれぞれの説明です。  
  
|名前|説明|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|Unicode 文字の ASCII 文字エンコードを表します。|  
|<xref:System.Text.UnicodeEncoding>|Unicode 文字の UTF-16 エンコーディングを表します。|  
|<xref:System.Text.UTF32Encoding>|Unicode 文字の UTF-32 エンコーディングを表します。|  
|<xref:System.Text.UTF7Encoding>|Unicode 文字の UTF-7 エンコードを表します。|  
|<xref:System.Text.UTF8Encoding>|Unicode 文字の UTF-8 エンコードを表します。|  
  
## <a name="see-also"></a>関連項目  
 [ファイルの読み取り](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [ファイルへの書き込み](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
