---
title: "方法 : 文字列内を検索する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a>方法 : 文字列内を検索する (Visual Basic)
この例では、<xref:System.String.IndexOf%2A>メソッドを<xref:System.String>部分文字列の最初に見つかった位置のインデックスを報告するオブジェクト。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `Imports`ステートメントを指定する、<xref:System>名前空間。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 <xref:System.String.IndexOf%2A>メソッドは、最初に見つかった部分文字列の最初の文字の位置を報告します。 インデックスには、文字列の最初の文字が 0 のインデックスは、0 から始まります。  
  
 場合<xref:System.String.IndexOf%2A>、部分文字列が見つからない-1 を返します。  
  
 <xref:System.String.IndexOf%2A>メソッドは大文字小文字を区別し、現在のカルチャを使用します。  
  
 最適なエラー コントロールの文字列の検索をする可能性があります、`Try`のブロック、[を再試行してください.キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)構築します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.String.IndexOf%2A>  
 [Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [文字列](../../../../visual-basic/programming-guide/language-features/strings/index.md)
