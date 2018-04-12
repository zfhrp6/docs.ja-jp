---
title: プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07233ed1c68f85878ffdd7131f64e30e158dc350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="110e7-102">プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました</span><span class="sxs-lookup"><span data-stu-id="110e7-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="110e7-103">プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="110e7-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="110e7-104">このため、XML IntelliSense は使用できません。</span><span class="sxs-lookup"><span data-stu-id="110e7-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="110e7-105">プロジェクトに含まれる XML スキーマ定義 (XSD) スキーマでエラーがあります。</span><span class="sxs-lookup"><span data-stu-id="110e7-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="110e7-106">このエラーは、既存の XSD スキーマと競合していますが、プロジェクトに設定されている XSD スキーマ (.xsd) ファイルを追加するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="110e7-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="110e7-107">**エラー ID:** BC36810</span><span class="sxs-lookup"><span data-stu-id="110e7-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="110e7-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="110e7-108">To correct this error</span></span>  
  
-   <span data-ttu-id="110e7-109">警告をダブルクリック、**エラー一覧**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="110e7-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="110e7-110">Visual Basic では、警告のソースである XSD ファイルの場所を実行します。</span><span class="sxs-lookup"><span data-stu-id="110e7-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="110e7-111">XSD スキーマでエラーを修正します。</span><span class="sxs-lookup"><span data-stu-id="110e7-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="110e7-112">必要なすべての XSD スキーマ (.xsd) ファイルがプロジェクトに含まれることを確認します。</span><span class="sxs-lookup"><span data-stu-id="110e7-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="110e7-113">をクリックする必要があります**すべてのファイル**上、**プロジェクト**にファイルを .xsd を表示するメニュー**ソリューション エクスプ ローラー**です。</span><span class="sxs-lookup"><span data-stu-id="110e7-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="110e7-114">.Xsd ファイルを右クリックし、をクリックして**プロジェクトに含める**プロジェクトのファイルをインクルードします。</span><span class="sxs-lookup"><span data-stu-id="110e7-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="110e7-115">XML to Schema ウィザードを使用している場合、同じソースから複数回のスキーマを推論する場合にこのエラーが発生することができます。</span><span class="sxs-lookup"><span data-stu-id="110e7-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="110e7-116">スキーマ項目テンプレートに新しい XML がここでは、既存の XSD スキーマ ファイルを削除するには、プロジェクトから追加し、XML to Schema ウィザードに提供適用可能なすべての XML ソース プロジェクトのします。</span><span class="sxs-lookup"><span data-stu-id="110e7-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="110e7-117">XSD スキーマでエラーを識別できない場合、XML コンパイラはエラー メッセージの詳細を提供するための十分な情報ことはできません。</span><span class="sxs-lookup"><span data-stu-id="110e7-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="110e7-118">場合に、プロジェクトの一致に含まれる .xsd ファイル用の XML 名前空間が、Visual Studio での XML スキーマで特定された XML 名前空間を使用することを確認する詳細なエラー情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="110e7-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110e7-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="110e7-119">See Also</span></span>  
 <span data-ttu-id="110e7-120">[[エラー一覧] ウィンドウ](/visualstudio/ide/reference/error-list-window)</span><span class="sxs-lookup"><span data-stu-id="110e7-120">[Error List Window](/visualstudio/ide/reference/error-list-window)</span></span>  
 [<span data-ttu-id="110e7-121">XML</span><span class="sxs-lookup"><span data-stu-id="110e7-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
