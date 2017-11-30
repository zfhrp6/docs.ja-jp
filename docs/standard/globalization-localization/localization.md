---
title: "ローカリゼーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4aaf2da77a1fab55cbebd6bfa05a2b1c74e5cbbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="localization"></a><span data-ttu-id="7c3f9-102">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="7c3f9-102">Localization</span></span>
<span data-ttu-id="7c3f9-103">ローカライズは、アプリケーションのリソースをアプリケーションでサポートされる各カルチャのローカライズ版に変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="7c3f9-104">完了後にのみローカライズの手順に進む必要があります、[ローカライズ化のレビュー](../../../docs/standard/globalization-localization/localizability-review.md)グローバライズされたアプリケーションがローカライズ可能であることを確認する手順。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>  
  
 <span data-ttu-id="7c3f9-105">ローカライズ可能なアプリケーションは、2 つの概念ブロック、すべてのユーザー インターフェイス要素を格納するブロックと実行可能コードを格納するブロックに分割されます。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-105">An application that is ready for localization is separated into two conceptual blocks, a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="7c3f9-106">ユーザー インターフェイス ブロックには、文字列、エラー メッセージ、ダイアログ ボックス、メニューのニュートラル カルチャについての埋め込みオブジェクト リソースなどのローカライズ可能なユーザー インターフェイス要素のみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="7c3f9-107">コード ブロックには、サポートされているすべてのカルチャが使用するアプリケーション コードだけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="7c3f9-108">共通言語ランタイムには、そのリソースからアプリケーションの実行可能コードを分離するサテライト アセンブリ リソース モデルがサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="7c3f9-109">このモデルの実装の詳細については、次を参照してください。[デスクトップ アプリでのリソース](../../../docs/framework/resources/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-109">For more information about implementing this model, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="7c3f9-110">アプリケーションの各ローカライズ バージョンでは、ローカライズされたユーザー インターフェイス ブロックが、ターゲット カルチャに適切な言語に翻訳を含む新しいサテライト アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="7c3f9-111">すべてのカルチャのコード ブロックは同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="7c3f9-112">ユーザー インターフェイスを使用してブロックのコード ブロックのローカライズされたバージョンの組み合わせには、アプリケーションのローカライズされたバージョンが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>  
  
 <span data-ttu-id="7c3f9-113">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]ターゲットのカルチャに対して Windows フォームをすばやくローカライズできるようにする Windows フォーム リソース エディター (Winres.exe) を提供します。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="7c3f9-114">このツールの使用方法の詳細については、次を参照してください。 [Winres.exe (Windows フォーム リソース エディター)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)です。</span><span class="sxs-lookup"><span data-stu-id="7c3f9-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c3f9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c3f9-115">See Also</span></span>  
 [<span data-ttu-id="7c3f9-116">グローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="7c3f9-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="7c3f9-117">ローカライズ化の確認</span><span class="sxs-lookup"><span data-stu-id="7c3f9-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 [<span data-ttu-id="7c3f9-118">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="7c3f9-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="7c3f9-119">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="7c3f9-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
