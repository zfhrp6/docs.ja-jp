---
title: "&quot;Extension&quot; 属性は &quot;Module&quot;、&quot;Sub&quot; または &quot;Function&quot; の宣言にのみ適用できます。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
dev_langs:
- VB
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 18
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e88241180fe1320bfd1db90a38a9a7560ae3dead
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="3df21-102">'Extension' 属性は 'Module'、'Sub' または 'Function' の宣言にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="3df21-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="3df21-103">Visual Basic でのデータ型を拡張する唯一の方法では、標準のモジュール内の拡張メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="3df21-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="3df21-104">拡張メソッドになる、`Sub`プロシージャまたは`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="3df21-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="3df21-105">すべての拡張メソッドは、拡張属性でマークする必要があります`<Extension()>`から、<xref:System.Runtime.CompilerServices?displayProperty=fullName>名前空間</xref:System.Runtime.CompilerServices?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="3df21-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="3df21-106">必要に応じて、拡張メソッドを格納しているモジュールの場合は、同じ方法でマークされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3df21-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="3df21-107">拡張属性の他の使用が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="3df21-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="3df21-108">**エラー ID:** BC36550</span><span class="sxs-lookup"><span data-stu-id="3df21-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3df21-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3df21-109">To correct this error</span></span>  
  
-   <span data-ttu-id="3df21-110">拡張属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="3df21-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="3df21-111">外側のモジュールで定義されている、方法として、拡張機能を設計し直します。</span><span class="sxs-lookup"><span data-stu-id="3df21-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3df21-112">例</span><span class="sxs-lookup"><span data-stu-id="3df21-112">Example</span></span>  
 <span data-ttu-id="3df21-113">次の例、`Print`のメソッド、`String`データ型。</span><span class="sxs-lookup"><span data-stu-id="3df21-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3df21-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3df21-114">See Also</span></span>  
 <span data-ttu-id="3df21-115">[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="3df21-115">[Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="3df21-116"> [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="3df21-116"> [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span></span>  
<span data-ttu-id="3df21-117"> [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)</span><span class="sxs-lookup"><span data-stu-id="3df21-117"> [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)</span></span>

