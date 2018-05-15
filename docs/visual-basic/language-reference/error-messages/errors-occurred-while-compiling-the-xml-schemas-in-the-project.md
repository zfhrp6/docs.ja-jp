---
title: プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 0cc565809792c619ca9903f9ef9b029b51a8aa17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="1fb70-102">プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました</span><span class="sxs-lookup"><span data-stu-id="1fb70-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="1fb70-103">プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1fb70-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="1fb70-104">このため、XML IntelliSense は使用できません。</span><span class="sxs-lookup"><span data-stu-id="1fb70-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="1fb70-105">プロジェクトに含まれる XML スキーマ定義 (XSD) スキーマでエラーがあります。</span><span class="sxs-lookup"><span data-stu-id="1fb70-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="1fb70-106">このエラーは、既存の XSD スキーマと競合していますが、プロジェクトに設定されている XSD スキーマ (.xsd) ファイルを追加するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="1fb70-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="1fb70-107">**エラー ID:** BC36810</span><span class="sxs-lookup"><span data-stu-id="1fb70-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1fb70-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1fb70-108">To correct this error</span></span>  
  
-   <span data-ttu-id="1fb70-109">警告をダブルクリック、**エラー一覧**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="1fb70-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="1fb70-110">Visual Basic では、警告のソースである XSD ファイルの場所を実行します。</span><span class="sxs-lookup"><span data-stu-id="1fb70-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="1fb70-111">XSD スキーマでエラーを修正します。</span><span class="sxs-lookup"><span data-stu-id="1fb70-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="1fb70-112">必要なすべての XSD スキーマ (.xsd) ファイルがプロジェクトに含まれることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1fb70-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="1fb70-113">をクリックする必要があります**すべてのファイル**上、**プロジェクト**にファイルを .xsd を表示するメニュー**ソリューション エクスプ ローラー**です。</span><span class="sxs-lookup"><span data-stu-id="1fb70-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="1fb70-114">.Xsd ファイルを右クリックし、をクリックして**プロジェクトに含める**プロジェクトのファイルをインクルードします。</span><span class="sxs-lookup"><span data-stu-id="1fb70-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="1fb70-115">XML to Schema ウィザードを使用している場合、同じソースから複数回のスキーマを推論する場合にこのエラーが発生することができます。</span><span class="sxs-lookup"><span data-stu-id="1fb70-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="1fb70-116">スキーマ項目テンプレートに新しい XML がここでは、既存の XSD スキーマ ファイルを削除するには、プロジェクトから追加し、XML to Schema ウィザードに提供適用可能なすべての XML ソース プロジェクトのします。</span><span class="sxs-lookup"><span data-stu-id="1fb70-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="1fb70-117">XSD スキーマでエラーを識別できない場合、XML コンパイラはエラー メッセージの詳細を提供するための十分な情報ことはできません。</span><span class="sxs-lookup"><span data-stu-id="1fb70-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="1fb70-118">場合に、プロジェクトの一致に含まれる .xsd ファイル用の XML 名前空間が、Visual Studio での XML スキーマで特定された XML 名前空間を使用することを確認する詳細なエラー情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="1fb70-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb70-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fb70-119">See Also</span></span>  
 <span data-ttu-id="1fb70-120">[[エラー一覧] ウィンドウ](/visualstudio/ide/reference/error-list-window)</span><span class="sxs-lookup"><span data-stu-id="1fb70-120">[Error List Window](/visualstudio/ide/reference/error-list-window)</span></span>  
 [<span data-ttu-id="1fb70-121">XML</span><span class="sxs-lookup"><span data-stu-id="1fb70-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
