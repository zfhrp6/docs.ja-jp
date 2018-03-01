---
title: "TextFieldParser は空白を含むコメント トークンをサポートしていません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e5f41b1f1019459d55d5806f45301f4248e65fc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-whitespace"></a><span data-ttu-id="af87b-102">TextFieldParser は空白を含むコメント トークンをサポートしていません</span><span class="sxs-lookup"><span data-stu-id="af87b-102">TextFieldParser does not support comment tokens that contain whitespace</span></span>
<span data-ttu-id="af87b-103">空白を含むコメント トークンが指定されています。</span><span class="sxs-lookup"><span data-stu-id="af87b-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="af87b-104">トークンの先頭に空白がある場合を除き、 `TextFieldParser` は空白を含むコメント トークンをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="af87b-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="af87b-105">トークンの先頭にある空白は無視されます。</span><span class="sxs-lookup"><span data-stu-id="af87b-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af87b-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="af87b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="af87b-107">適切なコメント トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="af87b-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af87b-108">参照</span><span class="sxs-lookup"><span data-stu-id="af87b-108">See Also</span></span>  
 [<span data-ttu-id="af87b-109">TextFieldParser.CommentTokens プロパティ</span><span class="sxs-lookup"><span data-stu-id="af87b-109">TextFieldParser.CommentTokens Property</span></span>](http://msdn.microsoft.com/library/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)  
 [<span data-ttu-id="af87b-110">TextFieldParser オブジェクトによるテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="af87b-110">Parsing Text Files with the TextFieldParser Object</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [<span data-ttu-id="af87b-111">TextFieldParser オブジェクト</span><span class="sxs-lookup"><span data-stu-id="af87b-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
