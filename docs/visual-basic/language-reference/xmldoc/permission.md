---
title: "&lt;アクセス許可&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 67e11998e43a43f92c26eb5f7daa488d288823c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="d4811-102">&lt;アクセス許可&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4811-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="d4811-103">メンバーの必要なアクセス許可を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4811-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4811-104">構文</span><span class="sxs-lookup"><span data-stu-id="d4811-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4811-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4811-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="d4811-106">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="d4811-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d4811-107">コンパイラは、指定されたコード要素が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4811-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="d4811-108">囲む`member`引用符 ("") です。</span><span class="sxs-lookup"><span data-stu-id="d4811-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d4811-109">メンバーへのアクセスの説明です。</span><span class="sxs-lookup"><span data-stu-id="d4811-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4811-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d4811-110">Remarks</span></span>  
 <span data-ttu-id="d4811-111">使用して、`<permission>`タグ メンバーへのアクセスを文書化します。</span><span class="sxs-lookup"><span data-stu-id="d4811-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="d4811-112">使用して、<xref:System.Security.PermissionSet>クラス メンバーへのアクセスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4811-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="d4811-113">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="d4811-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4811-114">例</span><span class="sxs-lookup"><span data-stu-id="d4811-114">Example</span></span>  
 <span data-ttu-id="d4811-115">この例では、`<permission>`を記述するタグ、<xref:System.Security.Permissions.FileIOPermission>で必要な`ReadFile`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d4811-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d4811-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4811-116">See Also</span></span>  
 [<span data-ttu-id="d4811-117">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="d4811-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
