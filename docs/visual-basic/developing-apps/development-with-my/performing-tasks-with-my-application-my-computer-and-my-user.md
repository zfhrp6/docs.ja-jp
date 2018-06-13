---
title: My.Application、My.Computer、および My.User でのタスクの実行 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: bc2b0521598c00cdb398d936d61d65874a9cf274
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583397"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="6cb14-102">My.Application、My.Computer、および My.User でのタスクの実行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cb14-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="6cb14-103">次の 3 つの中央`My`へのアクセスについてよく使用される機能を提供するオブジェクトは`My.Application`(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>)、 `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)、および`My.User`(<xref:Microsoft.VisualBasic.ApplicationServices.User>)。</span><span class="sxs-lookup"><span data-stu-id="6cb14-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="6cb14-104">これらのオブジェクトを使用して、それぞれ、現在のアプリケーション、アプリケーションにインストールされているコンピューターまたはアプリケーションの現在のユーザーに関連する情報にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="6cb14-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="6cb14-105">My.Application、My.Computer、および My.User</span><span class="sxs-lookup"><span data-stu-id="6cb14-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="6cb14-106">次の例では、情報をする方法を示しますを使用して取得`My`です。</span><span class="sxs-lookup"><span data-stu-id="6cb14-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="6cb14-107">情報を取得するだけでなくこれら 3 つのオブジェクトを介して公開されるメンバーも、そのオブジェクトに関連するメソッドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="6cb14-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="6cb14-108">インスタンスのさまざまなファイルを操作または経由でのレジストリを更新する方法を表示できます`My.Computer`です。</span><span class="sxs-lookup"><span data-stu-id="6cb14-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="6cb14-109">ファイル I/O は簡単かつ短時間では大幅に`My`さまざまなファイル、ディレクトリ、およびドライブを操作のメソッドとプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6cb14-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="6cb14-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser>オブジェクトは、大きな構造化されたファイルが区切られたまたは固定幅フィールドから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="6cb14-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="6cb14-111">この例を開いて、`TextFieldParser``reader`からの読み取りを使用して`C:\TestFolder1\test1.txt`です。</span><span class="sxs-lookup"><span data-stu-id="6cb14-111">This example opens the `TextFieldParser``reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="6cb14-112">`My.Application` アプリケーションのカルチャを変更できます。</span><span class="sxs-lookup"><span data-stu-id="6cb14-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="6cb14-113">次の例では、このメソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6cb14-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6cb14-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6cb14-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [<span data-ttu-id="6cb14-115">プロジェクトの種類に応じた My の機能</span><span class="sxs-lookup"><span data-stu-id="6cb14-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
