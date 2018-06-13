---
title: '&#39;拡張機能&#39;属性にのみ適用できます&#39;モジュール&#39;、 &#39;Sub&#39;、または&#39;関数&#39;宣言'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587320"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="65dce-102">&#39;拡張機能&#39;属性にのみ適用できます&#39;モジュール&#39;、 &#39;Sub&#39;、または&#39;関数&#39;宣言</span><span class="sxs-lookup"><span data-stu-id="65dce-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="65dce-103">Visual Basic でのデータ型を拡張する唯一の方法では、標準的なモジュールの中に拡張メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="65dce-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="65dce-104">拡張メソッドを指定できます、`Sub`プロシージャまたは`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="65dce-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="65dce-105">すべての拡張メソッドは、拡張属性と共に設定されなければなりません`<Extension()>`から、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="65dce-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="65dce-106">必要に応じて、拡張メソッドを含むモジュールの場合は、同じ方法でマークされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65dce-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="65dce-107">拡張属性の他の使用が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="65dce-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="65dce-108">**エラー ID:** BC36550</span><span class="sxs-lookup"><span data-stu-id="65dce-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65dce-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="65dce-109">To correct this error</span></span>  
  
-   <span data-ttu-id="65dce-110">拡張属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="65dce-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="65dce-111">それを囲むモジュールで定義されている、メソッドとして、拡張機能を設計し直します。</span><span class="sxs-lookup"><span data-stu-id="65dce-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65dce-112">例</span><span class="sxs-lookup"><span data-stu-id="65dce-112">Example</span></span>  
 <span data-ttu-id="65dce-113">次の例では定義、`Print`のメソッド、`String`データ型。</span><span class="sxs-lookup"><span data-stu-id="65dce-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="65dce-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="65dce-114">See Also</span></span>  
 [<span data-ttu-id="65dce-115">属性の概要</span><span class="sxs-lookup"><span data-stu-id="65dce-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="65dce-116">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="65dce-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="65dce-117">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="65dce-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
