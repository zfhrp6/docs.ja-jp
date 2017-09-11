---
title: "方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a43fb764e6a1ba0a2f1ad1645624c9d8a55bc858
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="e8561-102">方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e8561-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="e8561-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> 名前空間の <xref:Microsoft.VisualBasic?displayProperty=fullName> メソッドを使用すると、Windows でのファイル操作に関する進行状況を示す標準ダイアログ ボックスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="e8561-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="e8561-104">Visual Studio で参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="e8561-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="e8561-105">メニュー バーで、**[プロジェクト]**、**[参照の追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="e8561-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="e8561-106">**[参照マネージャー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8561-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="e8561-107">**[アセンブリ]** で、**[フレームワーク]** を選択します (選択されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="e8561-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="e8561-108">名前の一覧で、**[Microsoft.VisualBasic]** のチェック ボックスをオンにし、**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e8561-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8561-109">例</span><span class="sxs-lookup"><span data-stu-id="e8561-109">Example</span></span>  
 <span data-ttu-id="e8561-110">次のコードは、`sourcePath` で指定されたディレクトリを `destinationPath` で指定されたディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e8561-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="e8561-111">また、操作の完了までに必要な残りの予測時間を示す、標準的なダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="e8561-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 <span data-ttu-id="e8561-112">[!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e8561-112">[!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8561-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8561-113">See Also</span></span>  
 [<span data-ttu-id="e8561-114">ファイル システムとレジストリ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e8561-114">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)

