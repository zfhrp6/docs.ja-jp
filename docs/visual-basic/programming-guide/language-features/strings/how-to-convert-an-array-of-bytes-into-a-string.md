---
title: '方法 : Visual Basic でバイトの配列を文字列に変換する'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: c22ae89322230d8a98ae3ae2c1485e73456e0a7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="131eb-102">方法 : Visual Basic でバイトの配列を文字列に変換する</span><span class="sxs-lookup"><span data-stu-id="131eb-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="131eb-103">このトピックでは、バイト配列からバイトを文字列に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="131eb-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="131eb-104">例</span><span class="sxs-lookup"><span data-stu-id="131eb-104">Example</span></span>  
 <span data-ttu-id="131eb-105">この例では、<xref:System.Text.Encoding.GetString%2A>のメソッド、<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>バイト配列からすべてのバイトを文字列に変換するクラスをエンコードします。</span><span class="sxs-lookup"><span data-stu-id="131eb-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 <span data-ttu-id="131eb-106">バイト配列を文字列に変換する場合、エンコーディング オプションから選択できます。</span><span class="sxs-lookup"><span data-stu-id="131eb-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="131eb-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>します。 セットを取得 ASCII (7 ビット) 文字のエンコードします。</span><span class="sxs-lookup"><span data-stu-id="131eb-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="131eb-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: ビッグ エンディアン バイト順を使用する utf-16 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="131eb-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="131eb-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: システムの現在の ANSI コード ページのエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="131eb-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="131eb-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: リトル エンディアン バイト順を使用する utf-16 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="131eb-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="131eb-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: リトル エンディアン バイト順を使用する utf-32 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="131eb-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="131eb-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Utf-7 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="131eb-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="131eb-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Utf-8 形式のエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="131eb-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131eb-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="131eb-114">See Also</span></span>  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetString%2A>  
 [<span data-ttu-id="131eb-115">方法: 文字列を Visual Basic でバイト配列に変換</span><span class="sxs-lookup"><span data-stu-id="131eb-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
