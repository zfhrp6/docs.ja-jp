---
title: '方法 : Visual Basic で列挙型を反復処理する'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646579"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="fa6e4-102">方法 : Visual Basic で列挙型を反復処理する</span><span class="sxs-lookup"><span data-stu-id="fa6e4-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="fa6e4-103">一連の関連する定数を操作する場合や、定数値に名前を関連付ける場合は、列挙型を使うと便利です。</span><span class="sxs-lookup"><span data-stu-id="fa6e4-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="fa6e4-104">列挙体を反復処理に移動できますが使用して、配列、<xref:System.Enum.GetValues%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fa6e4-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="fa6e4-105">使用して、列挙型を反復処理することも、`For...Each`ステートメントを使用して、<xref:System.Enum.GetNames%2A>または<xref:System.Enum.GetValues%2A>文字列または数値の値を抽出する方法です。</span><span class="sxs-lookup"><span data-stu-id="fa6e4-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="fa6e4-106">列挙体を反復処理するには</span><span class="sxs-lookup"><span data-stu-id="fa6e4-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="fa6e4-107">配列を宣言し、列挙型に変換して、<xref:System.Enum.GetValues%2A>メソッドとして、配列を渡す前に、他の変数です。</span><span class="sxs-lookup"><span data-stu-id="fa6e4-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="fa6e4-108">次の例には、列挙体の各メンバーが表示されます。<xref:Microsoft.VisualBasic.FirstDayOfWeek>ように、列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="fa6e4-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fa6e4-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa6e4-109">See Also</span></span>  
 [<span data-ttu-id="fa6e4-110">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="fa6e4-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="fa6e4-111">方法: 列挙型を宣言</span><span class="sxs-lookup"><span data-stu-id="fa6e4-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="fa6e4-112">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="fa6e4-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="fa6e4-113">方法 : 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="fa6e4-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="fa6e4-114">方法 : 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="fa6e4-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="fa6e4-115">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="fa6e4-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="fa6e4-116">配列</span><span class="sxs-lookup"><span data-stu-id="fa6e4-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
