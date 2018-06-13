---
title: SaveFileDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: be5f70e2e8b0d5143ef387819689ce95564a72d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537448"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="47784-102">SaveFileDialog コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="47784-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="47784-103">Windows フォームの <xref:System.Windows.Forms.SaveFileDialog> コンポーネントは、事前構成済みのダイアログ ボックスです。</span><span class="sxs-lookup"><span data-stu-id="47784-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="47784-104">標準と同じである**ファイルを保存** ダイアログ ボックスの Windows で使用します。</span><span class="sxs-lookup"><span data-stu-id="47784-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="47784-105">これは、<xref:System.Windows.Forms.CommonDialog> クラスを継承しています。</span><span class="sxs-lookup"><span data-stu-id="47784-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="47784-106">SaveFileDialog コンポーネントの操作</span><span class="sxs-lookup"><span data-stu-id="47784-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="47784-107">独自のダイアログ ボックスを構成する代わりにファイルを保存するユーザーを有効にするための簡易ソリューションとして使用します。</span><span class="sxs-lookup"><span data-stu-id="47784-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="47784-108">標準の Windows ダイアログ ボックスには、この証明書利用者で作成したアプリケーションの基本機能は、ユーザーにすぐに慣れるです。</span><span class="sxs-lookup"><span data-stu-id="47784-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="47784-109">ただし、ときに使用して、<xref:System.Windows.Forms.SaveFileDialog>コンポーネント、独自のファイルの保存ロジックを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47784-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="47784-110">使用することができます、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドを実行時に、ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="47784-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="47784-111">読み取り/書き込みモードを使用してファイルを開くことができます、<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="47784-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="47784-112">フォームに追加されたとき、<xref:System.Windows.Forms.SaveFileDialog>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。</span><span class="sxs-lookup"><span data-stu-id="47784-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47784-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="47784-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="47784-114">SaveFileDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="47784-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
