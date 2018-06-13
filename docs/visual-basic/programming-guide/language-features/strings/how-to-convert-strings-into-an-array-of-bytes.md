---
title: '方法 : Visual Basic で文字列をバイトの配列に変換する'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: da4a47b955b91f4bb39ecd7832da30d76e75d553
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647954"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>方法 : Visual Basic で文字列をバイトの配列に変換する
このトピックでは、文字列をバイト配列に変換する方法を示します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Text.Encoding.GetBytes%2A>のメソッド、<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>バイトの配列を文字列に変換するクラスをエンコードします。  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 バイト配列に文字列に変換する場合、エンコーディング オプションから選択できます。  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>します。 セットを取得 ASCII (7 ビット) 文字のエンコードします。  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: ビッグ エンディアン バイト順を使用する utf-16 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: システムの現在の ANSI コード ページのエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: リトル エンディアン バイト順を使用する utf-16 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: リトル エンディアン バイト順を使用する utf-32 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Utf-7 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Utf-8 形式のエンコーディングを取得します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [方法: Visual Basic で文字列のバイト配列に変換](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
