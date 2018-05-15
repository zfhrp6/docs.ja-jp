---
title: '方法 : Visual Basic でファイル名とパスを検証する'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: ab3df335bc5bba21d386bb69b12d840990e629fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="5c306-102">方法 : Visual Basic でファイル名とパスを検証する</span><span class="sxs-lookup"><span data-stu-id="5c306-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="5c306-103">この例を返します、`Boolean`文字列が、ファイル名またはパスを表すかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="5c306-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="5c306-104">検証では、名前に、ファイル システムで許可されない文字が含まれるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="5c306-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c306-105">例</span><span class="sxs-lookup"><span data-stu-id="5c306-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 <span data-ttu-id="5c306-106">この例では、名前の位置が正しくないコロン、またはディレクトリ名がない場合、または名の長さがシステム定義の最大長を超える場合はチェックしません。</span><span class="sxs-lookup"><span data-stu-id="5c306-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="5c306-107">または確認しません、アプリケーションが、指定した名前のファイル システム リソースにアクセスする権限を持つかどうかです。</span><span class="sxs-lookup"><span data-stu-id="5c306-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c306-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c306-108">See Also</span></span>  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [<span data-ttu-id="5c306-109">Visual Basic における文字列の検証</span><span class="sxs-lookup"><span data-stu-id="5c306-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
