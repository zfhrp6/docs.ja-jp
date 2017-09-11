---
title: "方法 : レガシ エンコーディングと Unicode の間で変換を行う (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], legacy to unicode encoding
- strings [C#], converting between encodings
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a016f4ab7de25eec408243cb9b467f9255556bba
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-between-legacy-encodings-and-unicode-c-programming-guide"></a><span data-ttu-id="eae7e-102">方法 : レガシ エンコーディングと Unicode の間で変換を行う (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="eae7e-102">How to: Convert Between Legacy Encodings and Unicode (C# Programming Guide)</span></span>
<span data-ttu-id="eae7e-103">C# では、メモリ内の文字列はすべて Unicode (UTF-16) としてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="eae7e-103">In C#, all strings in memory are encoded as Unicode (UTF-16).</span></span> <span data-ttu-id="eae7e-104">データをストレージから `string` オブジェクトに取り込むと、そのデータは UTF-16 に自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="eae7e-104">When you bring data from storage into a `string` object, the data is automatically converted to UTF-16.</span></span> <span data-ttu-id="eae7e-105">データに含まれるのが 0 ～ 127 の ASCII 値のみの場合は、変換の際にユーザー側が特別な処理を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="eae7e-105">If the data contains only ASCII values from 0 through 127, the conversion requires no extra effort on your part.</span></span> <span data-ttu-id="eae7e-106">ただし、ソース テキストに拡張 ASCII バイト値 (128 ～ 255) が含まれる場合、既定では、現在のコード ページに従って拡張文字が解釈されます。</span><span class="sxs-lookup"><span data-stu-id="eae7e-106">However, if the source text contains extended ASCII byte values (128 through 255), the extended characters will be interpreted by default according to the current code page.</span></span> <span data-ttu-id="eae7e-107">ソース テキストが別のコード ページに従って解釈されるように指定するには、次の例に示すように、<xref:System.Text.Encoding?displayProperty=fullName> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="eae7e-107">To specify that the source text should be interpreted according to a different code page, use the <xref:System.Text.Encoding?displayProperty=fullName> class as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eae7e-108">例</span><span class="sxs-lookup"><span data-stu-id="eae7e-108">Example</span></span>  
 <span data-ttu-id="eae7e-109">次の例は、8 ビット ASCII でエンコードされているテキスト ファイルを変換し、Windows コード ページ 737 に従ってソース テキストを解釈する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="eae7e-109">The following example shows how to convert a text file that has been encoded in 8-bit ASCII, interpreting the source text according to Windows Code Page 737.</span></span>  
  
 <span data-ttu-id="eae7e-110">[!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="eae7e-110">[!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae7e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="eae7e-111">See Also</span></span>  
 [<span data-ttu-id="eae7e-112">文字列</span><span class="sxs-lookup"><span data-stu-id="eae7e-112">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

