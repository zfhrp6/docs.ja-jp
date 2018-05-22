---
title: Storeadm.exe (分離ストレージ ツール)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c9b8d0680a50d9945bef0d03d10e45750fc49a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="c82d3-102">Storeadm.exe (分離ストレージ ツール)</span><span class="sxs-lookup"><span data-stu-id="c82d3-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="c82d3-103">分離ストレージ ツールは、現在のユーザーに関するすべての既存ストアの一覧表示または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="c82d3-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="c82d3-104">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="c82d3-105">このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="c82d3-106">詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c82d3-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="c82d3-107">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c82d3-108">構文</span><span class="sxs-lookup"><span data-stu-id="c82d3-108">Syntax</span></span>  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c82d3-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c82d3-109">Parameters</span></span>  
  
|<span data-ttu-id="c82d3-110">オプション</span><span class="sxs-lookup"><span data-stu-id="c82d3-110">Option</span></span>|<span data-ttu-id="c82d3-111">説明</span><span class="sxs-lookup"><span data-stu-id="c82d3-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c82d3-112">**/h****[elp]**</span><span class="sxs-lookup"><span data-stu-id="c82d3-112">**/h**[**elp**]</span></span>|<span data-ttu-id="c82d3-113">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="c82d3-114">**/list**</span><span class="sxs-lookup"><span data-stu-id="c82d3-114">**/list**</span></span>|<span data-ttu-id="c82d3-115">現在のユーザーに関するすべての既存ストアを表示します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="c82d3-116">このユーザーによって実行された、すべてのアプリケーションまたはアセンブリに関するストアなどが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="c82d3-117">**/machine**</span><span class="sxs-lookup"><span data-stu-id="c82d3-117">**/machine**</span></span>|<span data-ttu-id="c82d3-118">コンピューター ストアを選択します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-118">Selects the machine store.</span></span> <span data-ttu-id="c82d3-119">このオプションを **/list** または **/remove** オプションと一緒に使用すると、それらのアクションをマシン ストアに適用する必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="c82d3-120">.NET Framework 2.0 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="c82d3-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="c82d3-121">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="c82d3-121">**/quiet**</span></span>|<span data-ttu-id="c82d3-122">クワイエット モードを指定します。このモードでは、情報の出力が中止され、エラー メッセージだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="c82d3-123">**/remove**</span><span class="sxs-lookup"><span data-stu-id="c82d3-123">**/remove**</span></span>|<span data-ttu-id="c82d3-124">現在のユーザーに関するすべての既存ストアを削除します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="c82d3-125">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="c82d3-125">**/roaming**</span></span>|<span data-ttu-id="c82d3-126">ローミング ストアを選択します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-126">Selects the roaming store.</span></span> <span data-ttu-id="c82d3-127">このオプションを **/list** または **/remove** オプションと一緒に使用すると、それらのアクションをローミング ストアに適用する必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="c82d3-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="c82d3-128">**/?**</span></span>|<span data-ttu-id="c82d3-129">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c82d3-130">コメント</span><span class="sxs-lookup"><span data-stu-id="c82d3-130">Remarks</span></span>  
 <span data-ttu-id="c82d3-131">オプションを指定せずにコマンド ラインから Storeadm.exe を実行すると、Storeadm.exe に関する構文とオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="c82d3-132">一般に、**/list** オプションと **/remove** オプションは同時に使用されますが、2 つ以上のオプションを指定した場合、それらのオプションはコマンド ラインに表示されている順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="c82d3-133">アプリケーションは、ユーザー ストアまたはコンピューター ストアのいずれかを選択して保存できます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
-   <span data-ttu-id="c82d3-134">ローカル ストアは、該当するユーザーに関するデータのローミングが有効な場合でも、ローミングされないことが保証されている場所 (Windows 2000 以降) に存在します。</span><span class="sxs-lookup"><span data-stu-id="c82d3-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
-   <span data-ttu-id="c82d3-135">ローミング ストアは、ローミングできる場所に存在しますが、ローミングできるのは、Windows NT の管理機能を通じて、該当するユーザーに対してローミングが有効化されている場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
-   <span data-ttu-id="c82d3-136">コンピューター ストアは、コンピューターのすべてのユーザーに共通で、コンピューターの共通ディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c82d3-137">コンピューター ストアは .NET Framework Version 2.0 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="c82d3-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="c82d3-138">ユーザーに対してローミングが実際に有効になっているかどうかは、Storeadm.exe の管理に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="c82d3-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="c82d3-139">オプションを指定せずに Storeadm.exe を実行した場合、すべてのアクションがローカル ストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="c82d3-140">**/roaming** オプションを指定した場合は、すべてのアクションが、ローミングできるストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="c82d3-141">**/machine** オプションを指定してこのツールを実行すると、すべてのアクションがコンピューター ストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c82d3-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82d3-142">参照</span><span class="sxs-lookup"><span data-stu-id="c82d3-142">See Also</span></span>  
 [<span data-ttu-id="c82d3-143">ツール</span><span class="sxs-lookup"><span data-stu-id="c82d3-143">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="c82d3-144">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="c82d3-144">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="c82d3-145">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="c82d3-145">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
