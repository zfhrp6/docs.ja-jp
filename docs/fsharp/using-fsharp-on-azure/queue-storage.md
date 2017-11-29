---
title: "F# を使用して Azure キュー ストレージの概要します。"
description: "Azure キューでは、アプリケーション コンポーネント間で信頼性の高い非同期メッセージングを提供します。 クラウドを単独でスケーリングのアプリケーション コンポーネントのメッセージングを有効します。"
keywords: "visual f#、f#、関数型プログラミングでは、.NET では、.NET Core では、Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 70dc554c-8f4d-42a7-8e2a-6438657d012a
ms.openlocfilehash: f5ebdb3f3b50996a397c8420b773178493744d70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="19439-105">F# を使用して Azure キュー ストレージの概要します。</span><span class="sxs-lookup"><span data-stu-id="19439-105">Get started with Azure Queue storage using F#</span></span> #

<span data-ttu-id="19439-106">Azure キュー ストレージは、クラウド アプリケーションのコンポーネント間のメッセージングを提供します。</span><span class="sxs-lookup"><span data-stu-id="19439-106">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="19439-107">スケールのアプリケーションを設計するには、アプリケーション コンポーネントは多くの場合、切り離されて、それらを個別に拡張できるようにします。</span><span class="sxs-lookup"><span data-stu-id="19439-107">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="19439-108">キュー ストレージは、クラウド、デスクトップ、社内設置のサーバー、またはモバイル デバイスで実行されているかどうか、アプリケーション コンポーネント間の通信用の非同期メッセージングを提供します。</span><span class="sxs-lookup"><span data-stu-id="19439-108">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="19439-109">キュー ストレージには、非同期タスクを管理して、プロセスのワークフローの構築もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="19439-109">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="19439-110">このチュートリアルについて</span><span class="sxs-lookup"><span data-stu-id="19439-110">About this tutorial</span></span>

<span data-ttu-id="19439-111">このチュートリアルでは、Azure キュー ストレージを使用した一般的なタスクの f# コードを記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="19439-111">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="19439-112">作成してキューを削除して追加する、読み取り、およびキューのメッセージを削除する、以下のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="19439-112">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="19439-113">キュー ストレージの概念的な概要を参照してください[キューを格納する .NET ガイド](/azure/storage/storage-dotnet-how-to-use-queues)です。</span><span class="sxs-lookup"><span data-stu-id="19439-113">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="19439-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="19439-114">Prerequisites</span></span>

<span data-ttu-id="19439-115">このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)です。</span><span class="sxs-lookup"><span data-stu-id="19439-115">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="19439-116">ストレージ アクセス キーは、このアカウントにも必要です。</span><span class="sxs-lookup"><span data-stu-id="19439-116">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="19439-117">作成、f# スクリプトと開始 f# 対話型</span><span class="sxs-lookup"><span data-stu-id="19439-117">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="19439-118">この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="19439-118">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="19439-119">F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`queues.fsx`、f# 開発環境でします。</span><span class="sxs-lookup"><span data-stu-id="19439-119">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="19439-120">次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="19439-120">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="19439-121">名前空間の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="19439-121">Add namespace declarations</span></span>

<span data-ttu-id="19439-122">次の追加`open`ステートメントの先頭に、`queues.fsx`ファイル。</span><span class="sxs-lookup"><span data-stu-id="19439-122">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="19439-123">接続文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="19439-123">Get your connection string</span></span>

<span data-ttu-id="19439-124">このチュートリアルでは、Azure ストレージ接続文字列を必要があります。</span><span class="sxs-lookup"><span data-stu-id="19439-124">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="19439-125">接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。</span><span class="sxs-lookup"><span data-stu-id="19439-125">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="19439-126">このチュートリアルでは、スクリプトでは、次のように、接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="19439-126">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="19439-127">ただし、これは**しないで**実際のプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="19439-127">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="19439-128">ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="19439-128">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="19439-129">常に、ストレージ アカウント キーを保護するように注意します。</span><span class="sxs-lookup"><span data-stu-id="19439-129">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="19439-130">ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。</span><span class="sxs-lookup"><span data-stu-id="19439-130">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="19439-131">侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。</span><span class="sxs-lookup"><span data-stu-id="19439-131">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="19439-132">実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。</span><span class="sxs-lookup"><span data-stu-id="19439-132">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="19439-133">構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="19439-133">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="19439-134">Azure 構成マネージャーを使用することはオプションです。</span><span class="sxs-lookup"><span data-stu-id="19439-134">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="19439-135">.NET Framework のなどの API を使用することも`ConfigurationManager`型です。</span><span class="sxs-lookup"><span data-stu-id="19439-135">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="19439-136">接続文字列を解析します。</span><span class="sxs-lookup"><span data-stu-id="19439-136">Parse the connection string</span></span>

<span data-ttu-id="19439-137">接続文字列を解析するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="19439-137">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="19439-138">これは、戻り値は、`CloudStorageAccount`です。</span><span class="sxs-lookup"><span data-stu-id="19439-138">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="19439-139">キュー サービス クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="19439-139">Create the Queue service client</span></span>

<span data-ttu-id="19439-140">`CloudQueueClient`クラスでは、キュー ストレージに格納されているキューを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="19439-140">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="19439-141">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="19439-141">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="19439-142">キュー ストレージからデータを読み書きするコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="19439-142">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="19439-143">キューを作成します。</span><span class="sxs-lookup"><span data-stu-id="19439-143">Create a queue</span></span>

<span data-ttu-id="19439-144">この例では、存在しない場合は、キューを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="19439-144">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="19439-145">キューにメッセージを挿入します。</span><span class="sxs-lookup"><span data-stu-id="19439-145">Insert a message into a queue</span></span>

<span data-ttu-id="19439-146">既存のキューにメッセージを挿入するに最初に作成する新しい`CloudQueueMessage`です。</span><span class="sxs-lookup"><span data-stu-id="19439-146">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="19439-147">次に、呼び出し、`AddMessage`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="19439-147">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="19439-148">A`CloudQueueMessage`から作成することか、形式の文字列 (utf-8) または`byte`次のように、配列。</span><span class="sxs-lookup"><span data-stu-id="19439-148">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="19439-149">次のメッセージをピークする方法</span><span class="sxs-lookup"><span data-stu-id="19439-149">Peek at the next message</span></span>

<span data-ttu-id="19439-150">呼び出すことによって、キューから削除することがなくキュー、前面のメッセージをピークすることができます、`PeekMessage`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="19439-150">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="19439-151">処理のため次のメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="19439-151">Get the next message for processing</span></span>

<span data-ttu-id="19439-152">処理のため、キューの先頭にあるメッセージを取得するには呼び出すことによって、`GetMessage`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="19439-152">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="19439-153">使用して、メッセージを正常に処理を後で示す`DeleteMessage`です。</span><span class="sxs-lookup"><span data-stu-id="19439-153">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="19439-154">キューに置かれたメッセージの内容を変更します。</span><span class="sxs-lookup"><span data-stu-id="19439-154">Change the contents of a queued message</span></span>

<span data-ttu-id="19439-155">取得したメッセージ内の場所のキューに内容を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="19439-155">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="19439-156">メッセージは、作業のタスクを表している場合は、作業タスクの状態を更新するこの機能を使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="19439-156">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="19439-157">次のコードでは、新しいコンテンツを含むキューのメッセージを更新し、もう 1 つの 60 秒を拡張する表示タイムアウトを設定します。</span><span class="sxs-lookup"><span data-stu-id="19439-157">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="19439-158">これは、メッセージに関連付けられている作業の状態を保存し、により、クライアント メッセージで作業を続行する別の分。</span><span class="sxs-lookup"><span data-stu-id="19439-158">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="19439-159">ハードウェアまたはソフトウェアの障害により、処理手順が失敗した場合に、最初からやり直すことがなくキューのメッセージで複数のステップのワークフローを追跡するために、この手法を使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="19439-159">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="19439-160">通常、同様に、再試行カウントを保持するができますし、削除は、メッセージが複数回を超える再試行された場合。</span><span class="sxs-lookup"><span data-stu-id="19439-160">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="19439-161">これは、アプリケーション エラーが処理されるたびにトリガーをメッセージから保護します。</span><span class="sxs-lookup"><span data-stu-id="19439-161">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="19439-162">次のメッセージをキューから削除</span><span class="sxs-lookup"><span data-stu-id="19439-162">De-queue the next message</span></span>

<span data-ttu-id="19439-163">コード 2 つの手順で、キューからメッセージをキューします。</span><span class="sxs-lookup"><span data-stu-id="19439-163">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="19439-164">呼び出すと`GetMessage`キュー内の次のメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="19439-164">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="19439-165">返されたメッセージ`GetMessage`このキューからメッセージを読み取るその他のコードを非表示になります。</span><span class="sxs-lookup"><span data-stu-id="19439-165">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="19439-166">既定では、このメッセージでは 30 秒間の非表示に維持されます。</span><span class="sxs-lookup"><span data-stu-id="19439-166">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="19439-167">完了するには、キューからメッセージを削除する必要がありますも呼び出す`DeleteMessage`です。</span><span class="sxs-lookup"><span data-stu-id="19439-167">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="19439-168">メッセージを削除するには、この 2 段階プロセスでは、コードは、ハードウェアまたはソフトウェアの障害によりメッセージの処理に失敗すると、コードの別のインスタンスは、同じメッセージを取得し、もう一度やり直してくださいことを保証します。</span><span class="sxs-lookup"><span data-stu-id="19439-168">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="19439-169">コードの呼び出し`DeleteMessage`直後に、メッセージが処理されました。</span><span class="sxs-lookup"><span data-stu-id="19439-169">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="19439-170">非同期のワークフローを使用して、共通のキュー ストレージ Api</span><span class="sxs-lookup"><span data-stu-id="19439-170">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="19439-171">この例では、共通のキュー ストレージ Api の非同期ワークフローを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="19439-171">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="19439-172">キューから取り出すメッセージの追加オプション</span><span class="sxs-lookup"><span data-stu-id="19439-172">Additional options for de-queuing messages</span></span>

<span data-ttu-id="19439-173">キューからメッセージの取得をカスタマイズする 2 つの方法はあります。</span><span class="sxs-lookup"><span data-stu-id="19439-173">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="19439-174">最初に、(最大 32 個) のメッセージのバッチを取得できます。</span><span class="sxs-lookup"><span data-stu-id="19439-174">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="19439-175">第二に、長いまたは短い非表示タイムアウトを設定する、詳細や、各メッセージを完全に処理にかかる時間が、コードを許可します。</span><span class="sxs-lookup"><span data-stu-id="19439-175">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="19439-176">次のコード例では`GetMessages`20 を取得する 1 つのメッセージを呼び出すし、それぞれのメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="19439-176">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="19439-177">また、メッセージごとに 5 分間に非表示タイムアウトを設定します。</span><span class="sxs-lookup"><span data-stu-id="19439-177">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="19439-178">呼び出し以降後 5 分が経過している 5 分間は、同時にすべてのメッセージの開始を`GetMessages`、削除されていないすべてのメッセージが可視になります。</span><span class="sxs-lookup"><span data-stu-id="19439-178">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="19439-179">キューの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="19439-179">Get the queue length</span></span>

<span data-ttu-id="19439-180">キュー内のメッセージの数の推定値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="19439-180">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="19439-181">`FetchAttributes`メソッドは、メッセージ数など、キューの属性を取得するキュー サービスを確認します。</span><span class="sxs-lookup"><span data-stu-id="19439-181">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="19439-182">`ApproximateMessageCount`プロパティによって取得された最後の値を返します、`FetchAttributes`メソッドを呼び出さずに、キュー サービス。</span><span class="sxs-lookup"><span data-stu-id="19439-182">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="19439-183">キューを削除します。</span><span class="sxs-lookup"><span data-stu-id="19439-183">Delete a queue</span></span>

<span data-ttu-id="19439-184">削除するキューとそれに含まれるすべてのメッセージを呼び出し、`Delete`キュー オブジェクトのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="19439-184">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="19439-185">次のステップ</span><span class="sxs-lookup"><span data-stu-id="19439-185">Next steps</span></span>

<span data-ttu-id="19439-186">キュー ストレージの基本を学習したようになりましたことはより複雑な記憶域タスクについて学習するこれらのリンクに従います。</span><span class="sxs-lookup"><span data-stu-id="19439-186">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="19439-187">参照を .NET 用 storage クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="19439-187">Storage Client Library for .NET reference</span></span>](http://go.microsoft.com/fwlink/?LinkID=390731&clcid=0x409)
- [<span data-ttu-id="19439-188">Azure ストレージの型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="19439-188">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="19439-189">Azure ストレージ チーム ブログ</span><span class="sxs-lookup"><span data-stu-id="19439-189">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="19439-190">接続文字列を構成します。</span><span class="sxs-lookup"><span data-stu-id="19439-190">Configuring Connection Strings</span></span>](http://msdn.microsoft.com/library/azure/ee758697.aspx)
- [<span data-ttu-id="19439-191">REST API リファレンス</span><span class="sxs-lookup"><span data-stu-id="19439-191">REST API reference</span></span>](http://msdn.microsoft.com/library/azure/dd179355)
