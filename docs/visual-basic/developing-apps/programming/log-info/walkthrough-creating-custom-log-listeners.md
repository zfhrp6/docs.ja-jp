---
title: "カスタム ログ リスナーの作成 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: 19
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bc6fde8dcbb27157f3fd180ad393bb406222195e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="8b7d2-102">チュートリアル: カスタム ログ リスナーの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b7d2-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="8b7d2-103">このチュートリアルでは、カスタム ログ リスナーを作成する方法と、`My.Application.Log` オブジェクトの出力を待機するように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="8b7d2-104">作業の開始</span><span class="sxs-lookup"><span data-stu-id="8b7d2-104">Getting Started</span></span>  
 <span data-ttu-id="8b7d2-105">ログ リスナーは、<xref:System.Diagnostics.TraceListener> クラスから継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="8b7d2-106">リスナーを作成するには</span><span class="sxs-lookup"><span data-stu-id="8b7d2-106">To create the listener</span></span>  
  
-   <span data-ttu-id="8b7d2-107">アプリケーションで、<xref:System.Diagnostics.TraceListener> を継承する `SimpleListener` という名前のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     <span data-ttu-id="8b7d2-108">[!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8b7d2-108">[!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]</span></span>  
  
     <span data-ttu-id="8b7d2-109"><xref:System.Diagnostics.TraceListener.Write%2A> および <xref:System.Diagnostics.TraceListener.WriteLine%2A> メソッド (基底クラスに必須) は、`MsgBox` を呼び出して入力された値を表示します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-109">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="8b7d2-110"><xref:System.Security.Permissions.HostProtectionAttribute> 属性は、<xref:System.Diagnostics.TraceListener.Write%2A> および <xref:System.Diagnostics.TraceListener.WriteLine%2A> メソッドに適用されます。これは、各メソッドの属性を基底クラスのメソッドに一致させるためです。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="8b7d2-111"><xref:System.Security.Permissions.HostProtectionAttribute> 属性を使用すると、コードを実行するホストは、コードがホスト保護の同期を公開していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b7d2-112"><xref:System.Security.Permissions.HostProtectionAttribute> 属性は、共通言語ランタイムをホストし、ホスト保護を実装している SQL Server などのアンマネージ アプリケーションでのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-112">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="8b7d2-113">`My.Application.Log` でログ リスナーが使用されるようにするには、ログ リスナーを含むアセンブリに厳密な名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-113">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="8b7d2-114">次の手順では、厳密な名前付きのログ リスナー アセンブリを作成するための簡単な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-114">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="8b7d2-115">詳しくは、「[厳密な名前付きアセンブリの作成と使用](https://msdn.microsoft.com/library/xwb8f617)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-115">For more information, see [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="8b7d2-116">ログ リスナー アセンブリに厳密な名前を付けるには</span><span class="sxs-lookup"><span data-stu-id="8b7d2-116">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="8b7d2-117">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8b7d2-118">**[プロジェクト]** メニューの **[プロパティ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-118">On the **Project** menu, choose **Properties**.</span></span> <span data-ttu-id="8b7d2-119">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-119">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="8b7d2-120">**[署名]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-120">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="8b7d2-121">**[アセンブリの署名]** ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-121">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="8b7d2-122">**[厳密な名前のキー ファイルを選択してください]** ドロップダウン リストから **[\<新規作成>]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-122">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="8b7d2-123">**[厳密な名前キーの作成]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-123">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="8b7d2-124">**[キー ファイル名]** ボックスで、キー ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-124">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="8b7d2-125">**[パスワードの入力]** および **[パスワードの確認入力]** ボックスにパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-125">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="8b7d2-126">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-126">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="8b7d2-127">アプリケーションをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-127">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="8b7d2-128">リスナーの追加</span><span class="sxs-lookup"><span data-stu-id="8b7d2-128">Adding the Listener</span></span>  
 <span data-ttu-id="8b7d2-129">アセンブリに厳密な名前を付けたら、次はリスナーの厳密な名前を確認して、`My.Application.Log` でログ リスナーが使用されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-129">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="8b7d2-130">厳密な名前を持つ型の書式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-130">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="8b7d2-131">\<型名>, \<アセンブリ名>, \<バージョン番号>, \<カルチャ>, \<厳密な名前></span><span class="sxs-lookup"><span data-stu-id="8b7d2-131">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="8b7d2-132">リスナーの厳密な名前を確認するには</span><span class="sxs-lookup"><span data-stu-id="8b7d2-132">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="8b7d2-133">次のコードは、厳密に名前指定された `SimpleListener` の型名を確認する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-133">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     <span data-ttu-id="8b7d2-134">[!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8b7d2-134">[!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]</span></span>  
  
     <span data-ttu-id="8b7d2-135">型の厳密な名前は、プロジェクトによって変わります。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-135">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="8b7d2-136">厳密な名前を使用すると、リスナーを `My.Application.Log` のログ リスナー コレクションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-136">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="8b7d2-137">My.Application.Log にリスナーを追加するには</span><span class="sxs-lookup"><span data-stu-id="8b7d2-137">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="8b7d2-138">**ソリューション エクスプローラー** で app.config を右クリックし、 **[開く]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-138">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="8b7d2-139">または</span><span class="sxs-lookup"><span data-stu-id="8b7d2-139">-or-</span></span>  
  
     <span data-ttu-id="8b7d2-140">app.config ファイルがある場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-140">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="8b7d2-141">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-141">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="8b7d2-142">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-142">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="8b7d2-143">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-143">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="8b7d2-144">`<listeners>` セクション内にある、 `<source>` 属性が "DefaultSource" の `name` セクションで、 `<sources>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-144">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="8b7d2-145">`<sources>` セクションは、最上位の `<system.diagnostics>` セクション内の `<configuration>` セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-145">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="8b7d2-146">`<listeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-146">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="8b7d2-147">最上位の `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、 `<configuration>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-147">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="8b7d2-148">その `<sharedListeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-148">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="8b7d2-149">`SimpleLogStrongName` の値はリスナーの厳密な名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="8b7d2-149">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7d2-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b7d2-150">See Also</span></span>  
 <span data-ttu-id="8b7d2-151"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b7d2-151"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="8b7d2-152">[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="8b7d2-152">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="8b7d2-153">[方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="8b7d2-153">[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span></span>  
 <span data-ttu-id="8b7d2-154">[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="8b7d2-154">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 [<span data-ttu-id="8b7d2-155">チュートリアル : My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="8b7d2-155">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

