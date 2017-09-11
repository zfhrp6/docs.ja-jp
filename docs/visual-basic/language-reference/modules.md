---
title: "モジュール (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- modules, Visual Basic
ms.assetid: 370bfc90-e8f2-4942-bdec-9897ce605d31
caps.latest.revision: 11
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
ms.openlocfilehash: 808510c83339e1768dba39f119a2e97ac44f0e4a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="modules-visual-basic"></a><span data-ttu-id="5999d-102">モジュール (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5999d-102">Modules (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5999d-103">使用して、コードでは、文字列、数学的な計算をシステム情報の取得、ファイルおよびディレクトリの操作を実行する実行の操作などの一般的なタスクを簡単にするいくつかのモジュールを提供します。</span><span class="sxs-lookup"><span data-stu-id="5999d-103"> provides several modules that enable you to simplify common tasks in your code, including manipulating strings, performing mathematical calculations, getting system information, performing file and directory operations, and so on.</span></span> <span data-ttu-id="5999d-104">次の表に、によって提供されるモジュール[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="5999d-104">The following table lists the modules provided by [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="5999d-105"><xref:Microsoft.VisualBasic.Constants></xref:Microsoft.VisualBasic.Constants></span><span class="sxs-lookup"><span data-stu-id="5999d-105"><xref:Microsoft.VisualBasic.Constants></span></span>|<span data-ttu-id="5999d-106">その他の定数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5999d-106">Contains miscellaneous constants.</span></span> <span data-ttu-id="5999d-107">これらの定数は、コード内の任意の場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5999d-107">These constants can be used anywhere in your code.</span></span>|  
|<span data-ttu-id="5999d-108"><xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars></span><span class="sxs-lookup"><span data-stu-id="5999d-108"><xref:Microsoft.VisualBasic.ControlChars></span></span>|<span data-ttu-id="5999d-109">印刷してテキストを表示するための定数制御文字が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5999d-109">Contains constant control characters for printing and displaying text.</span></span>|  
|<span data-ttu-id="5999d-110"><xref:Microsoft.VisualBasic.Conversion></xref:Microsoft.VisualBasic.Conversion></span><span class="sxs-lookup"><span data-stu-id="5999d-110"><xref:Microsoft.VisualBasic.Conversion></span></span>|<span data-ttu-id="5999d-111">文字列、文字列から数値、および&1; つのデータに数値を別に入力を&10; 進数に変換するメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5999d-111">Contains members that convert decimal numbers to other bases, numbers to strings, strings to numbers, and one data type to another.</span></span>|  
|<span data-ttu-id="5999d-112"><xref:Microsoft.VisualBasic.DateAndTime></xref:Microsoft.VisualBasic.DateAndTime></span><span class="sxs-lookup"><span data-stu-id="5999d-112"><xref:Microsoft.VisualBasic.DateAndTime></span></span>|<span data-ttu-id="5999d-113">現在の日付または時刻の取得、日付計算の実行、日付または時刻を返す、日付または時刻の設定など、プロセスの時間メンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5999d-113">Contains members that get the current date or time, perform date calculations, return a date or time, set the date or time, or time the duration of a process.</span></span>|  
|<span data-ttu-id="5999d-114"><xref:Microsoft.VisualBasic.ErrObject></xref:Microsoft.VisualBasic.ErrObject></span><span class="sxs-lookup"><span data-stu-id="5999d-114"><xref:Microsoft.VisualBasic.ErrObject></span></span>|<span data-ttu-id="5999d-115">実行時エラーとを発生させる、またはエラーをクリアする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5999d-115">Contains information about run-time errors and methods to raise or clear an error.</span></span>|  
|<span data-ttu-id="5999d-116"><xref:Microsoft.VisualBasic.FileSystem></xref:Microsoft.VisualBasic.FileSystem></span><span class="sxs-lookup"><span data-stu-id="5999d-116"><xref:Microsoft.VisualBasic.FileSystem></span></span>|<span data-ttu-id="5999d-117">ファイル、ディレクトリまたはフォルダー、およびシステムの操作を実行するメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5999d-117">Contains members that perform file, directory or folder, and system operations.</span></span>|  
|<span data-ttu-id="5999d-118"><xref:Microsoft.VisualBasic.Financial></xref:Microsoft.VisualBasic.Financial></span><span class="sxs-lookup"><span data-stu-id="5999d-118"><xref:Microsoft.VisualBasic.Financial></span></span>|<span data-ttu-id="5999d-119">財務計算の実行に使用されるプロシージャが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5999d-119">Contains procedures that are used to perform financial calculations.</span></span>|  
|<span data-ttu-id="5999d-120"><xref:Microsoft.VisualBasic.Globals></xref:Microsoft.VisualBasic.Globals></span><span class="sxs-lookup"><span data-stu-id="5999d-120"><xref:Microsoft.VisualBasic.Globals></span></span>|<span data-ttu-id="5999d-121">現在のスクリプト エンジンのバージョンについてを説明します。</span><span class="sxs-lookup"><span data-stu-id="5999d-121">Contains information about the current scripting engine version.</span></span>|  
|<span data-ttu-id="5999d-122"><xref:Microsoft.VisualBasic.Information></xref:Microsoft.VisualBasic.Information></span><span class="sxs-lookup"><span data-stu-id="5999d-122"><xref:Microsoft.VisualBasic.Information></span></span>|<span data-ttu-id="5999d-123">返す、テスト、または配列のサイズや型名などの情報を確認するメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5999d-123">Contains the members that return, test for, or verify information such as array size, type names, and so on.</span></span>|  
|<span data-ttu-id="5999d-124"><xref:Microsoft.VisualBasic.Interaction></xref:Microsoft.VisualBasic.Interaction></span><span class="sxs-lookup"><span data-stu-id="5999d-124"><xref:Microsoft.VisualBasic.Interaction></span></span>|<span data-ttu-id="5999d-125">含むメンバーは、オブジェクト、アプリケーション、およびシステムと対話します。</span><span class="sxs-lookup"><span data-stu-id="5999d-125">Contains members interact with objects, applications, and systems.</span></span>|  
|<span data-ttu-id="5999d-126"><xref:Microsoft.VisualBasic.Strings></xref:Microsoft.VisualBasic.Strings></span><span class="sxs-lookup"><span data-stu-id="5999d-126"><xref:Microsoft.VisualBasic.Strings></span></span>|<span data-ttu-id="5999d-127">使用して、文字列、文字列の長さの取得、文字列の検索を再フォーマットなどの文字列操作を実行するメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5999d-127">Contains members that perform string operations such as reformatting strings, searching a string, getting the length of a string, and so on.</span></span>|  
|<span data-ttu-id="5999d-128"><xref:Microsoft.VisualBasic.VBMath></xref:Microsoft.VisualBasic.VBMath></span><span class="sxs-lookup"><span data-stu-id="5999d-128"><xref:Microsoft.VisualBasic.VBMath></span></span>|<span data-ttu-id="5999d-129">含むメンバーは、算術演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="5999d-129">Contains members perform mathematical operations.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5999d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5999d-130">See Also</span></span>  
 <span data-ttu-id="5999d-131">[Visual Basic 言語リファレンス](../../visual-basic/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5999d-131">[Visual Basic Language Reference](../../visual-basic/language-reference/index.md) </span></span>  
<span data-ttu-id="5999d-132"> [Visual Basic](../../visual-basic/index.md)</span><span class="sxs-lookup"><span data-stu-id="5999d-132"> [Visual Basic](../../visual-basic/index.md)</span></span>
