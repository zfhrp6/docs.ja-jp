---
title: 安全なコーディングのガイドライン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET Framework], security
- code security, options
- security-neutral code
- security [.NET Framework], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8d61e76a657c7341ec7dfcede6d7dc9943d4659
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588162"
---
# <a name="secure-coding-guidelines"></a><span data-ttu-id="821f1-102">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="821f1-102">Secure Coding Guidelines</span></span>
<span data-ttu-id="821f1-103">エビデンスベース セキュリティとコード アクセス セキュリティは、セキュリティを実現するための強力で明示的なメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="821f1-103">Evidence-based security and code access security provide very powerful, explicit mechanisms to implement security.</span></span> <span data-ttu-id="821f1-104">ほとんどのアプリケーション コードは、.NET Framework によって実装されるインフラストラクチャを単純に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="821f1-104">Most application code can simply use the infrastructure implemented by the .NET Framework.</span></span> <span data-ttu-id="821f1-105">場合によっては、アプリケーション特有の追加のセキュリティが必要になります。これは、セキュリティ システムを拡張するか、または新しい特有の方法を使用して構築されます。</span><span class="sxs-lookup"><span data-stu-id="821f1-105">In some cases, additional application-specific security is required, built either by extending the security system or by using new ad hoc methods.</span></span>  
  
 <span data-ttu-id="821f1-106">.NET Framework によって課されるアクセス許可やコード内で課される他の手段により防御機構を設けて、悪意のあるコードが知られたくない情報を入手したり、他の望ましくないアクションを実行したりすることを防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="821f1-106">Using the .NET Framework-enforced permissions and other enforcement in your code, you should erect barriers to prevent malicious code from obtaining information that you do not want it to have or performing other undesirable actions.</span></span> <span data-ttu-id="821f1-107">また、信頼されるコードを使用するすべての想定されるシナリオで、セキュリティと使いやすさのバランスを取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="821f1-107">Additionally, you must strike a balance between security and usability in all the expected scenarios using trusted code.</span></span>  
  
 <span data-ttu-id="821f1-108">この概要では、セキュリティ システムと連携するようコードを設計するさまざまな方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="821f1-108">This overview describes the different ways code can be designed to work with the security system.</span></span>  
  
## <a name="securing-resource-access"></a><span data-ttu-id="821f1-109">リソース アクセスの保護</span><span class="sxs-lookup"><span data-stu-id="821f1-109">Securing Resource Access</span></span>  
 <span data-ttu-id="821f1-110">コードを設計して作成する場合、作成元が不明なコードを使用したり呼び出したりする際は特に、コードがリソースに対して持つアクセス権の保護と制限を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="821f1-110">When designing and writing your code, you need to protect and limit the access that code has to resources, especially when using or invoking code of unknown origin.</span></span> <span data-ttu-id="821f1-111">そのため、コードの安全性を確保するために次の点に注意します。</span><span class="sxs-lookup"><span data-stu-id="821f1-111">So, keep in mind the following techniques to ensure your code is secure:</span></span>  
  
-   <span data-ttu-id="821f1-112">コード アクセス セキュリティ (CAS) を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="821f1-112">Do not use Code Access Security (CAS).</span></span>  
  
-   <span data-ttu-id="821f1-113">部分的に信頼されたコードを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="821f1-113">Do not use partial trusted code.</span></span>  
  
-   <span data-ttu-id="821f1-114">.NET リモート処理を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="821f1-114">Do not use .NET Remoting.</span></span>  
  
-   <span data-ttu-id="821f1-115">分散コンポーネント オブジェクト モデル (DCOM) を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="821f1-115">Do not use Distributed Component Object Model (DCOM).</span></span>  
  
-   <span data-ttu-id="821f1-116">バイナリ フォーマッタを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="821f1-116">Do not use binary formatters.</span></span>  
  
 <span data-ttu-id="821f1-117">部分的に信頼されたコードでは、コード アクセス セキュリティとセキュリティが透過的なコードはセキュリティ境界としてサポートされません。</span><span class="sxs-lookup"><span data-stu-id="821f1-117">Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code.</span></span> <span data-ttu-id="821f1-118">発生元の不明なコードの読み込みと実行に関しては、他のセキュリティ対策を適切に導入することなく行わないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="821f1-118">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="821f1-119">代わりのセキュリティ対策は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="821f1-119">The alternative security measures are:</span></span>  
  
-   <span data-ttu-id="821f1-120">仮想化</span><span class="sxs-lookup"><span data-stu-id="821f1-120">Virtualization</span></span>  
  
-   <span data-ttu-id="821f1-121">AppContainers</span><span class="sxs-lookup"><span data-stu-id="821f1-121">AppContainers</span></span>  
  
-   <span data-ttu-id="821f1-122">オペレーティング システム (OS) のユーザーおよびアクセス許可</span><span class="sxs-lookup"><span data-stu-id="821f1-122">Operating system (OS) users and permissions</span></span>  
  
-   <span data-ttu-id="821f1-123">Hyper-V コンテナー</span><span class="sxs-lookup"><span data-stu-id="821f1-123">Hyper-V containers</span></span>  
  
## <a name="security-neutral-code"></a><span data-ttu-id="821f1-124">セキュリティ中立なコード</span><span class="sxs-lookup"><span data-stu-id="821f1-124">Security-Neutral Code</span></span>  
 <span data-ttu-id="821f1-125">セキュリティ中立なコードは、セキュリティ システムに対して明示的な操作を何も行いません。</span><span class="sxs-lookup"><span data-stu-id="821f1-125">Security-neutral code does nothing explicit with the security system.</span></span> <span data-ttu-id="821f1-126">これは何であれ自分が受け取ったアクセス許可を使用して動作します。</span><span class="sxs-lookup"><span data-stu-id="821f1-126">It runs with whatever permissions it receives.</span></span> <span data-ttu-id="821f1-127">保護された操作 (ファイルの使用やネットワーキングなど) に関連したセキュリティ例外をアプリケーションがキャッチしなかった場合はハンドルされない例外になるとはいえ、セキュリティ中立なコードは .NET Framework のセキュリティ テクノロジを活用します。</span><span class="sxs-lookup"><span data-stu-id="821f1-127">Although applications that fail to catch security exceptions associated with protected operations (such as using files, networking, and so on) can result in an unhandled exception, security-neutral code still takes advantage of the .NET Framework security technologies.</span></span>  
  
 <span data-ttu-id="821f1-128">セキュリティ中立なライブラリは、理解しておくべき特別な特性を持っています。</span><span class="sxs-lookup"><span data-stu-id="821f1-128">A security-neutral library has special characteristics that you should understand.</span></span> <span data-ttu-id="821f1-129">ファイルを使用したり、アンマネージ コードを呼び出したりする API 要素をライブラリで提供していると仮定します。これらの操作に対応するアクセス許可を持っていないコードは、記述どおりに動作しません。</span><span class="sxs-lookup"><span data-stu-id="821f1-129">Suppose your library provides API elements that use files or call unmanaged code; if your code does not have the corresponding permission, it will not run as described.</span></span> <span data-ttu-id="821f1-130">しかし、コードがアクセス許可を持っているとしても、そのコードを呼び出すアプリケーション コードが同じアクセス許可を持っていなければ、正しく機能しません。</span><span class="sxs-lookup"><span data-stu-id="821f1-130">However, even if the code has the permission, any application code that calls it must have the same permission in order to work.</span></span> <span data-ttu-id="821f1-131">呼び出し元のコードに必要な権限がない場合、<xref:System.Security.SecurityException>コード アクセス セキュリティのスタック ウォークの結果として表示されます。</span><span class="sxs-lookup"><span data-stu-id="821f1-131">If the calling code does not have the right permission, a <xref:System.Security.SecurityException> appears as a result of the code access security stack walk.</span></span>  
  
## <a name="application-code-that-is-not-a-reusable-component"></a><span data-ttu-id="821f1-132">再利用可能なコンポーネントではないアプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="821f1-132">Application Code That Is Not a Reusable Component</span></span>  
 <span data-ttu-id="821f1-133">作成するコードがアプリケーションの一部であって、他のコードから呼び出されることがなければ、セキュリティは単純であり、特殊なコーディングは不要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="821f1-133">If your code is part of an application that will not be called by other code, security is simple and special coding might not be required.</span></span> <span data-ttu-id="821f1-134">ただし、悪意のあるコードがそのコードを呼び出す可能性があることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="821f1-134">However, remember that malicious code can call your code.</span></span> <span data-ttu-id="821f1-135">悪意のあるコードによるリソースへのアクセスをコード アクセス セキュリティが阻止する可能性もありますが、機密情報を含んだフィールドやプロパティの値をそのようなコードが読み取ることも考えられます。</span><span class="sxs-lookup"><span data-stu-id="821f1-135">While code access security might stop malicious code from accessing resources, such code could still read values of your fields or properties that might contain sensitive information.</span></span>  
  
 <span data-ttu-id="821f1-136">また、コードがインターネットやその他の信頼できないソースからのユーザー入力を受け付ける場合には、悪意のある入力にも注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="821f1-136">Additionally, if your code accepts user input from the Internet or other unreliable sources, you must be careful about malicious input.</span></span>  
  
## <a name="managed-wrapper-to-native-code-implementation"></a><span data-ttu-id="821f1-137">ネイティブ コードの実装のマネージ ラッパー</span><span class="sxs-lookup"><span data-stu-id="821f1-137">Managed Wrapper to Native Code Implementation</span></span>  
 <span data-ttu-id="821f1-138">一般にこのシナリオは、何らかの有用な機能がネイティブ コードで実装されており、これをマネージ コードで利用したいというケースに該当します。</span><span class="sxs-lookup"><span data-stu-id="821f1-138">Typically in this scenario, some useful functionality is implemented in native code that you want to make available to managed code.</span></span> <span data-ttu-id="821f1-139">マネージ ラッパーは、プラットフォーム呼び出しか COM 相互運用を使用して簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="821f1-139">Managed wrappers are easy to write using either platform invoke or COM interop.</span></span> <span data-ttu-id="821f1-140">ただしこの場合には、操作を成功させるために、ラッパーの呼び出し元がアンマネージ コードの権利を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="821f1-140">However, if you do this, callers of your wrappers must have unmanaged code rights in order to succeed.</span></span> <span data-ttu-id="821f1-141">つまり既定のポリシーでは、イントラネットやインターネットからダウンロードされたコードはラッパーでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="821f1-141">Under default policy, this means that code downloaded from an intranet or the Internet will not work with the wrappers.</span></span>  
  
 <span data-ttu-id="821f1-142">これらのラッパーを使用するすべてのアプリケーションにアンマネージ コードの権利を与えるよりも、これらの権利をラッパー コードのみに与える方が望ましいと言えます。</span><span class="sxs-lookup"><span data-stu-id="821f1-142">Instead of giving all applications that use these wrappers unmanaged code rights, it is better to give these rights only to the wrapper code.</span></span> <span data-ttu-id="821f1-143">基になる機能が何もリソースを公開しておらず、かつ実装も同様に安全である場合、ラッパーは、自分の権利をアサートしさえすれば、あらゆるコードが自分を通して呼び出しを行えるようにできます。</span><span class="sxs-lookup"><span data-stu-id="821f1-143">If the underlying functionality exposes no resources and the implementation is likewise safe, the wrapper only needs to assert its rights, which enables any code to call through it.</span></span> <span data-ttu-id="821f1-144">リソースが関係する場合のセキュリティ コーディングは、次のセクションで説明するライブラリ コードのケースと同じです。</span><span class="sxs-lookup"><span data-stu-id="821f1-144">When resources are involved, security coding should be the same as the library code case described in the next section.</span></span> <span data-ttu-id="821f1-145">ラッパーはこれらのリソースに対して呼び出し元を公開する可能性があるため、ネイティブ コードの安全性を慎重に確認する必要があり、その責任はラッパーにあります。</span><span class="sxs-lookup"><span data-stu-id="821f1-145">Because the wrapper is potentially exposing callers to these resources, careful verification of the safety of the native code is necessary and is the wrapper's responsibility.</span></span>  
  
## <a name="library-code-that-exposes-protected-resources"></a><span data-ttu-id="821f1-146">保護されたリソースを公開するライブラリ コード</span><span class="sxs-lookup"><span data-stu-id="821f1-146">Library Code That Exposes Protected Resources</span></span>  
 <span data-ttu-id="821f1-147">これはセキュリティ コーディングのアプローチとして最も強力なものであるため、方法を間違えるなら最も危険性の高いものともなります。ライブラリは他のコードに対し、(.NET Framework のクラスが使用するリソースのアクセス許可を課すのと同じように) 他の手段では使用できない特定のリソースにアクセスするためのインターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="821f1-147">This is the most powerful and hence potentially dangerous (if done incorrectly) approach for security coding: Your library serves as an interface for other code to access certain resources that are not otherwise available, just as the classes of the .NET Framework enforce permissions for the resources they use.</span></span> <span data-ttu-id="821f1-148">どこでリソースを公開しようと、コードはまずそのリソースに適したアクセス許可を要求し (つまりセキュリティ チェックを実行しなければなりません)、それから通常は実際の操作を実行するための権利をアサートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="821f1-148">Wherever you expose a resource, your code must first demand the permission appropriate to the resource (that is, it must perform a security check) and then typically assert its rights to perform the actual operation.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="821f1-149">関連トピック</span><span class="sxs-lookup"><span data-stu-id="821f1-149">Related Topics</span></span>  
  
|<span data-ttu-id="821f1-150">タイトル</span><span class="sxs-lookup"><span data-stu-id="821f1-150">Title</span></span>|<span data-ttu-id="821f1-151">説明</span><span class="sxs-lookup"><span data-stu-id="821f1-151">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="821f1-152">状態データの保護</span><span class="sxs-lookup"><span data-stu-id="821f1-152">Securing State Data</span></span>](../../../docs/standard/security/securing-state-data.md)|<span data-ttu-id="821f1-153">プライベート メンバーを保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="821f1-153">Describes how to protect private members.</span></span>|  
|[<span data-ttu-id="821f1-154">セキュリティとユーザー入力</span><span class="sxs-lookup"><span data-stu-id="821f1-154">Security and User Input</span></span>](../../../docs/standard/security/security-and-user-input.md)|<span data-ttu-id="821f1-155">ユーザー入力を受け取るアプリケーションのセキュリティ問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="821f1-155">Describes security concerns for applications that accept user input.</span></span>|  
|[<span data-ttu-id="821f1-156">セキュリティと競合状態</span><span class="sxs-lookup"><span data-stu-id="821f1-156">Security and Race Conditions</span></span>](../../../docs/standard/security/security-and-race-conditions.md)|<span data-ttu-id="821f1-157">コードで競合状態を回避する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="821f1-157">Describes how to avoid race conditions in your code.</span></span>|  
|[<span data-ttu-id="821f1-158">セキュリティと実行時のコード生成</span><span class="sxs-lookup"><span data-stu-id="821f1-158">Security and On-the-Fly Code Generation</span></span>](../../../docs/standard/security/security-and-on-the-fly-code-generation.md)|<span data-ttu-id="821f1-159">動的なコードを生成するアプリケーションのセキュリティ問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="821f1-159">Describes security concerns for applications that generate dynamic code.</span></span>|  
|[<span data-ttu-id="821f1-160">ロール ベースのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="821f1-160">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)|<span data-ttu-id="821f1-161">.NET Framework のロールベース セキュリティについて詳しく説明し、コードで使用するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="821f1-161">Describes .NET Framework role-based security in detail and provides instructions for using it in your code.</span></span>|
