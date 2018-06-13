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
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="b6c71-102">方法 : Visual Basic で文字列をバイトの配列に変換する</span><span class="sxs-lookup"><span data-stu-id="b6c71-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="b6c71-103">このトピックでは、文字列をバイト配列に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b6c71-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6c71-104">例</span><span class="sxs-lookup"><span data-stu-id="b6c71-104">Example</span></span>  
 <span data-ttu-id="b6c71-105">この例では、<xref:System.Text.Encoding.GetBytes%2A>のメソッド、<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>バイトの配列を文字列に変換するクラスをエンコードします。</span><span class="sxs-lookup"><span data-stu-id="b6c71-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 <span data-ttu-id="b6c71-106">バイト配列に文字列に変換する場合、エンコーディング オプションから選択できます。</span><span class="sxs-lookup"><span data-stu-id="b6c71-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
-   <span data-ttu-id="b6c71-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>します。 セットを取得 ASCII (7 ビット) 文字のエンコードします。</span><span class="sxs-lookup"><span data-stu-id="b6c71-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="b6c71-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: ビッグ エンディアン バイト順を使用する utf-16 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="b6c71-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="b6c71-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: システムの現在の ANSI コード ページのエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="b6c71-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="b6c71-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: リトル エンディアン バイト順を使用する utf-16 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="b6c71-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="b6c71-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: リトル エンディアン バイト順を使用する utf-32 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="b6c71-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="b6c71-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Utf-7 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="b6c71-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="b6c71-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Utf-8 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="b6c71-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c71-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6c71-114">See Also</span></span>  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [<span data-ttu-id="b6c71-115">方法: Visual Basic で文字列のバイト配列に変換</span><span class="sxs-lookup"><span data-stu-id="b6c71-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
