---
title: "方法: 列挙値に関連付けられている文字列を確認する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e2b0cfa6b1e426b38198581c7d493c8907b79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="db802-102">方法: 列挙値に関連付けられている文字列を確認する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db802-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="db802-103"><xref:System.Enum.GetValues%2A>と<xref:System.Enum.GetNames%2A>メソッドを使用する文字列と列挙型のメンバーに関連付けられている値を特定できます。</span><span class="sxs-lookup"><span data-stu-id="db802-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="db802-104">列挙体に関連付けられている文字列を決定するには</span><span class="sxs-lookup"><span data-stu-id="db802-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="db802-105">使用して、<xref:System.Enum.GetNames%2A>列挙型のメンバーに関連付けられている文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="db802-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="db802-106">この例は、列挙体を宣言`flavorEnum`を使用して、<xref:System.Enum.GetNames%2A>メソッドの各メンバーに関連付けられている文字列を表示します。</span><span class="sxs-lookup"><span data-stu-id="db802-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="db802-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="db802-107">See Also</span></span>  
 <xref:System.Enum.GetValues%2A>  
 <xref:System.Enum.GetNames%2A>  
 <xref:System.Enum>  
 [<span data-ttu-id="db802-108">方法: 列挙型を宣言</span><span class="sxs-lookup"><span data-stu-id="db802-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="db802-109">方法 : 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="db802-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="db802-110">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="db802-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="db802-111">方法: Visual Basic で列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="db802-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="db802-112">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="db802-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="db802-113">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="db802-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
