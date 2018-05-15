---
title: Visual Basic におけるオブジェクト変数
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 8383261c1806732c4c8abea9834000f003a848a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="0c8fa-102">Visual Basic におけるオブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="0c8fa-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="0c8fa-103">値を直接格納だけでなく、変数は、オブジェクトを参照できます。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="0c8fa-104">同じ理由から、変数に任意の値を代入するには、変数にオブジェクトを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="0c8fa-105">変数名は、多くの場合、メソッドと、オブジェクト自体にアクセスするために必要なプロパティの完全なパスよりも覚えやすくを短くします。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="0c8fa-106">オブジェクトを参照する変数を使用するは、繰り返しの必要なメソッドやプロパティを使って、オブジェクト自体にアクセスするよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="0c8fa-107">コードの実行中に、その他のオブジェクトを参照する変数を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="0c8fa-108">コードを短く</span><span class="sxs-lookup"><span data-stu-id="0c8fa-108">Making Code Shorter</span></span>  
 <span data-ttu-id="0c8fa-109">オブジェクト変数を使用すると、入力するのに必要があるコードを短縮します。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="0c8fa-110">次の例にアクセスするメソッドとプロパティの完全なパスを使用して、<xref:System.Windows.Forms.Control>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="0c8fa-111">このコードを短縮し、コントロールのオブジェクト変数を使用する場合、実行を高速化できます。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="0c8fa-112">特定のクラスに割り当てるしようとするオブジェクト変数を宣言する必要があります (`Control`ここで)。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="0c8fa-113">オブジェクトを変数に代入するとに参照するオブジェクトを処理するとまったく同じように扱うことできます。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="0c8fa-114">設定またはオブジェクトのプロパティを取得したり独自のメソッドのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="0c8fa-115">次の例では、オブジェクト変数を使用して、前の例のコードを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="0c8fa-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c8fa-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c8fa-116">See Also</span></span>  
 [<span data-ttu-id="0c8fa-117">変数宣言</span><span class="sxs-lookup"><span data-stu-id="0c8fa-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="0c8fa-118">方法 : 長い修飾パスを持つオブジェクトへのアクセス時間を短縮する</span><span class="sxs-lookup"><span data-stu-id="0c8fa-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [<span data-ttu-id="0c8fa-119">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="0c8fa-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="0c8fa-120">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="0c8fa-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="0c8fa-121">オブジェクト変数の値</span><span class="sxs-lookup"><span data-stu-id="0c8fa-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
