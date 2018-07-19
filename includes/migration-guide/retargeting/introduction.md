## <a name="introduction"></a><span data-ttu-id="05fd2-101">はじめに</span><span class="sxs-lookup"><span data-stu-id="05fd2-101">Introduction</span></span>
<span data-ttu-id="05fd2-102">変更の再ターゲットは、別の .NET Framework をターゲットとして再コンパイルされるアプリに影響します。</span><span class="sxs-lookup"><span data-stu-id="05fd2-102">Retargeting changes affect apps that are recompiled to target a different .NET Framework.</span></span> <span data-ttu-id="05fd2-103">Windows コモン コントロールには以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="05fd2-103">They include:</span></span>

* <span data-ttu-id="05fd2-104">デザイン時環境の変更。</span><span class="sxs-lookup"><span data-stu-id="05fd2-104">Changes in the design-time environment.</span></span> <span data-ttu-id="05fd2-105">たとえば、ビルド ツールは以前は出力しなかったときに警告を出力する場合があります。</span><span class="sxs-lookup"><span data-stu-id="05fd2-105">For example, build tools may emit warnings when previously they did not.</span></span>

* <span data-ttu-id="05fd2-106">ランタイム時環境の変更。</span><span class="sxs-lookup"><span data-stu-id="05fd2-106">Changes in the runtime environment.</span></span> <span data-ttu-id="05fd2-107">これらは、特に再ターゲットされた .NET Framework をターゲットとするアプリにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="05fd2-107">These affect only apps that specifically target the retargeted .NET Framework.</span></span> <span data-ttu-id="05fd2-108">.NET Framework の以前のバージョンを対象とするアプリは、それらのバージョンで実行されているときは以前のように動作します。</span><span class="sxs-lookup"><span data-stu-id="05fd2-108">Apps that target previous versions of the .NET Framework behave as they did when running under those versions.</span></span>

<span data-ttu-id="05fd2-109">変更の再ターゲットについて説明するトピックでは、次に示すように、予想される影響ごとに個々の項目を分類しました。</span><span class="sxs-lookup"><span data-stu-id="05fd2-109">In the topics that describe retargeting changes, we have classified individual items by their expected impact, as follows:</span></span>

<span data-ttu-id="05fd2-110">**メジャー** これは、多数のアプリに影響するか、またはコードに重大な変更を加える必要のある重要な変更点です。</span><span class="sxs-lookup"><span data-stu-id="05fd2-110">**Major** This is a significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="05fd2-111">**マイナー** これは、少数のアプリに影響するか、またはコードにわずかな変更を加える必要のある変更点です。</span><span class="sxs-lookup"><span data-stu-id="05fd2-111">**Minor** This is a change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="05fd2-112">**エッジ ケース** これは、一般的ではない特定のシナリオでアプリに影響する変更点です。</span><span class="sxs-lookup"><span data-stu-id="05fd2-112">**Edge case** This is a change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="05fd2-113">**透過的** これはアプリの開発者やユーザーには大きな影響を及ぼさない変更です。</span><span class="sxs-lookup"><span data-stu-id="05fd2-113">**Transparent** This is a change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="05fd2-114">アプリはこの変更のために変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="05fd2-114">The app should not require modification because of this change.</span></span>
