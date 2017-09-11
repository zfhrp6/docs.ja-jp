---
title: "属性 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- attributes [Visual Basic]
ms.assetid: 5deb2b8a-1afd-4dbd-8ee8-f093d74ad0eb
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d12b9e587d7b57998edff1559d24d0e7d4bda6ce
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="attributes-visual-basic"></a><span data-ttu-id="207ca-102">属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="207ca-102">Attributes (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="207ca-103">オブジェクトが、アンマネージ コードと相互運用できるようにするいくつかの属性と属性によって、モジュール名を指定せずにアクセスするモジュールのメンバーが&1; つ提供します。</span><span class="sxs-lookup"><span data-stu-id="207ca-103"> provides several attributes that allow objects interoperate with unmanaged code, and one attribute that enables module members to be accessed without the module name.</span></span> <span data-ttu-id="207ca-104">次の表で使用される属性[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="207ca-104">The following table lists the attributes used by [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="207ca-105"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="207ca-105"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>|<span data-ttu-id="207ca-106">クラスが COM オブジェクトとして公開できるようにするメタデータの追加をコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="207ca-106">Instructs the compiler to add metadata that allows a class to be exposed as a COM object.</span></span>|  
|<span data-ttu-id="207ca-107"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></xref:Microsoft.VisualBasic.HideModuleNameAttribute></span><span class="sxs-lookup"><span data-stu-id="207ca-107"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></span></span>|<span data-ttu-id="207ca-108">モジュール メンバーのモジュールに必要な修飾子のみを使用してアクセス許可します。</span><span class="sxs-lookup"><span data-stu-id="207ca-108">Allows the module members to be accessed using only the qualification needed for the module.</span></span>|  
|<span data-ttu-id="207ca-109"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span><span class="sxs-lookup"><span data-stu-id="207ca-109"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span></span>|<span data-ttu-id="207ca-110">構造体または非ローカル変数の配列を固定長の配列として処理することを示します。</span><span class="sxs-lookup"><span data-stu-id="207ca-110">Indicates that an array in a structure or non-local variable should be treated as a fixed-length array.</span></span>|  
|<span data-ttu-id="207ca-111"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></xref:Microsoft.VisualBasic.VBFixedStringAttribute></span><span class="sxs-lookup"><span data-stu-id="207ca-111"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></span></span>|<span data-ttu-id="207ca-112">固定長かのように文字列を処理することを示します。</span><span class="sxs-lookup"><span data-stu-id="207ca-112">Indicates that a string should be treated as if it were fixed length.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="207ca-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="207ca-113">See Also</span></span>  
 [<span data-ttu-id="207ca-114">属性の概要</span><span class="sxs-lookup"><span data-stu-id="207ca-114">Attributes overview</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)

