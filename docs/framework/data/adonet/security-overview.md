---
title: "セキュリティ Overview2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c952a79b70314ff9de195da322efd78d54176201
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="security-overview"></a><span data-ttu-id="65f0d-102">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="65f0d-102">Security Overview</span></span>
<span data-ttu-id="65f0d-103">アプリケーションのセキュリティ保護は継続的なプロセスとして行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-103">Securing an application is an ongoing process.</span></span> <span data-ttu-id="65f0d-104">開発者は、アプリケーションがあらゆる攻撃に対して安全であることを常に保証できるわけではありません。これは、新しい技術がもたらす未知の攻撃を予測することが不可能なためです。</span><span class="sxs-lookup"><span data-stu-id="65f0d-104">There will never be a point where a developer can guarantee that an application is safe from all attacks, because it is impossible to predict what kinds of future attacks new technologies will bring about.</span></span> <span data-ttu-id="65f0d-105">反対に、システムに欠陥が発見 (または公開) されていない場合も、そのシステムに欠陥がないとは限りません。</span><span class="sxs-lookup"><span data-stu-id="65f0d-105">Conversely, just because nobody has yet discovered (or published) security flaws in a system does not mean that none exist or could exist.</span></span> <span data-ttu-id="65f0d-106">プロジェクトの設計フェーズでセキュリティを考慮することはもちろんのこと、アプリケーションの使用期間を通じてセキュリティをいかに確保してゆくかを計画しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-106">You need to plan for security during the design phase of the project, as well as plan how security will be maintained over the lifetime of the application.</span></span>  
  
## <a name="design-for-security"></a><span data-ttu-id="65f0d-107">セキュリティのデザイン</span><span class="sxs-lookup"><span data-stu-id="65f0d-107">Design for Security</span></span>  
 <span data-ttu-id="65f0d-108">セキュリティで保護されたアプリケーションを開発するうえで最大の問題は、プロジェクトのコードが完成した後にセキュリティが導入されるということです。つまり、セキュリティが補足的になりがちです。</span><span class="sxs-lookup"><span data-stu-id="65f0d-108">One of the biggest problems in developing secure applications is that security is often an afterthought, something to implement after a project is code-complete.</span></span> <span data-ttu-id="65f0d-109">最初の段階でアプリケーションにセキュリティを導入しておかないと、十分な対策が講じられず、アプリケーションの安全性を損ねる結果となります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-109">Not building security into an application at the outset leads to insecure applications because little thought has been given to what makes an application secure.</span></span>  
  
 <span data-ttu-id="65f0d-110">最終段階でセキュリティが実装された場合、新しい制限によりソフトウェアが誤動作を起こしたり、予期していなかった機能を組み込むためにソフトウェアの書き換えが必要となって、バグの発生が増えます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-110">Last minute security implementation leads to more bugs, as software breaks under the new restrictions or has to be rewritten to accommodate unanticipated functionality.</span></span> <span data-ttu-id="65f0d-111">また、書き換えたすべてのコードが新たなバグの原因となる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-111">Every line of revised code contains the possibility of introducing a new bug.</span></span> <span data-ttu-id="65f0d-112">このような理由から、新しい機能の開発と平行して進めるよう、開発プロセスの早い段階でセキュリティを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-112">For this reason, you should consider security early in the development process so that it can proceed in tandem with the development of new features.</span></span>  
  
### <a name="threat-modeling"></a><span data-ttu-id="65f0d-113">脅威モデリング</span><span class="sxs-lookup"><span data-stu-id="65f0d-113">Threat Modeling</span></span>  
 <span data-ttu-id="65f0d-114">システムがどのような攻撃に曝されているかを理解せずに、攻撃からシステムを保護することはできません。</span><span class="sxs-lookup"><span data-stu-id="65f0d-114">You cannot protect a system against attack unless you understand all the potential attacks that it is exposed to.</span></span> <span data-ttu-id="65f0d-115">セキュリティ上の脅威を評価するプロセスと呼ばれる*脅威のモデリング*、尤度と、ADO.NET アプリケーションのセキュリティ侵害の影響を及ぼす可能性を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-115">The process of evaluating security threats, called *threat modeling*, is necessary to determine the likelihood and ramifications of security breaches in your ADO.NET application.</span></span>  
  
 <span data-ttu-id="65f0d-116">脅威のモデリングは、1) 攻撃者の視点を理解し、2) システムのセキュリティの特徴を把握し、3) 脅威を特定するという、大きく 3 つの手順で構成されます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-116">Threat modeling is composed of three high-level steps: understanding the adversary’s view, characterizing the security of the system, and determining threats.</span></span>  
  
 <span data-ttu-id="65f0d-117">脅威のモデリングでは、反復的なアプローチによってアプリケーションの脆弱性を評価しながら、最重要データの漏洩につながる最も危険な部分を特定します。</span><span class="sxs-lookup"><span data-stu-id="65f0d-117">Threat modeling is an iterative approach to assessing vulnerabilities in your application to find those that are the most dangerous because they expose the most sensitive data.</span></span> <span data-ttu-id="65f0d-118">脆弱性を特定したら、それらを深刻度の順にランクを付けて脅威への一連の対策に優先順位を付けます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-118">Once you identify the vulnerabilities, you rank them in order of severity and create a prioritized set of countermeasures to counter the threats.</span></span>  
  
 <span data-ttu-id="65f0d-119">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f0d-119">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="65f0d-120">リソース</span><span class="sxs-lookup"><span data-stu-id="65f0d-120">Resource</span></span>|<span data-ttu-id="65f0d-121">説明</span><span class="sxs-lookup"><span data-stu-id="65f0d-121">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="65f0d-122">[脅威のモデリング](http://go.microsoft.com/fwlink/?LinkId=98353)MSDN セキュリティ デベロッパー センター サイト</span><span class="sxs-lookup"><span data-stu-id="65f0d-122">The [Threat Modeling](http://go.microsoft.com/fwlink/?LinkId=98353) site on the MSDN Security Developer Center</span></span>|<span data-ttu-id="65f0d-123">脅威のモデリング プロセスを理解し、開発したアプリケーションの脅威モデルを構築するうえで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-123">The resources on this page will help you understand the threat modeling process and build threat models that you can use to secure your own applications</span></span>|  
  
## <a name="the-principle-of-least-privilege"></a><span data-ttu-id="65f0d-124">最小特権の原則</span><span class="sxs-lookup"><span data-stu-id="65f0d-124">The Principle of Least Privilege</span></span>  
 <span data-ttu-id="65f0d-125">アプリケーションの設計、ビルド、および配置は、アプリケーションが攻撃されるという前提で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-125">When you design, build, and deploy your application, you must assume that your application will be attacked.</span></span> <span data-ttu-id="65f0d-126">多くの場合、こうした攻撃は、コードを実行しているユーザーの権限で悪意のあるコードを実行することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-126">Often these attacks come from malicious code that executes with the permissions of the user running the code.</span></span> <span data-ttu-id="65f0d-127">高い技術を持った攻撃者が脆弱性を悪用することによって作成したコードも存在します。</span><span class="sxs-lookup"><span data-stu-id="65f0d-127">Others can originate with well-intentioned code that has been exploited by an attacker.</span></span> <span data-ttu-id="65f0d-128">セキュリティの計画を立てるときは、常に最悪のシナリオを想定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="65f0d-128">When planning security, always assume the worst-case scenario will occur.</span></span>  
  
 <span data-ttu-id="65f0d-129">コードを最小限の特権で実行することによって、できるだけ多層的にコードを防御することが対策の 1 つとして考えられます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-129">One counter-measure you can employ is to try to erect as many walls around your code as possible by running with least privilege.</span></span> <span data-ttu-id="65f0d-130">最小限の特権では、常に必要最小限のコードに対し、その処理に必要な最小限の時間だけ権限を与えることが原則となります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-130">The principle of least privilege says that any given privilege should be granted to the least amount of code necessary for the shortest duration of time that is required to get the job done.</span></span>  
  
 <span data-ttu-id="65f0d-131">安全なアプリケーションを作成するためのベスト プラクティスは、まず、権限をまったく付与しない状態から始め、その後で、実行しようとする特定のタスクに必要な最小限の権限を追加してゆくことです。</span><span class="sxs-lookup"><span data-stu-id="65f0d-131">The best practice for creating secure applications is to start with no permissions at all and then add the narrowest permissions for the particular task being performed.</span></span> <span data-ttu-id="65f0d-132">逆に、すべての権限を与えてから、不要なものを 1 つずつ拒否していく方法では、アプリケーションを危険にさらす結果となります。この場合、意図せずに必要以上の権限を付与することによってセキュリティ ホールを招く可能性があるため、安全性をテストすることも、管理していくことも困難です。</span><span class="sxs-lookup"><span data-stu-id="65f0d-132">By contrast, starting with all permissions and then denying individual ones leads to insecure applications that are difficult to test and maintain because security holes may exist from unintentionally granting more permissions than required.</span></span>  
  
 <span data-ttu-id="65f0d-133">アプリケーションのセキュリティ保護の詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f0d-133">For more information on securing your applications, see the following resources.</span></span>  
  
|<span data-ttu-id="65f0d-134">リソース</span><span class="sxs-lookup"><span data-stu-id="65f0d-134">Resource</span></span>|<span data-ttu-id="65f0d-135">説明</span><span class="sxs-lookup"><span data-stu-id="65f0d-135">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="65f0d-136">アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="65f0d-136">Securing Applications</span></span>](/visualstudio/ide/securing-applications)|<span data-ttu-id="65f0d-137">一般的なセキュリティ トピックへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="65f0d-137">Contains links to general security topics.</span></span> <span data-ttu-id="65f0d-138">分散アプリケーション、Web アプリケーション、モバイル アプリケーション、およびデスクトップ アプリケーションを保護するためのトピックへのリンクも含まれています。</span><span class="sxs-lookup"><span data-stu-id="65f0d-138">Also contains links to topics for securing distributed applications, Web applications, mobile applications, and desktop applications.</span></span>|  
  
## <a name="code-access-security-cas"></a><span data-ttu-id="65f0d-139">コード アクセス セキュリティ (CAS)</span><span class="sxs-lookup"><span data-stu-id="65f0d-139">Code Access Security (CAS)</span></span>  
 <span data-ttu-id="65f0d-140">コード アクセス セキュリティ (CAS) は、保護されたリソースや操作に対するコードのアクセスを制限するメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="65f0d-140">Code access security (CAS) is a mechanism that helps limit the access that code has to protected resources and operations.</span></span> <span data-ttu-id="65f0d-141">.NET Framework では CAS によって次の機能が実行されます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-141">In the .NET Framework, CAS performs the following functions:</span></span>  
  
-   <span data-ttu-id="65f0d-142">各種システム リソースにアクセスするための権限や権限セットを定義する。</span><span class="sxs-lookup"><span data-stu-id="65f0d-142">Defines permissions and permission sets that represent the right to access various system resources.</span></span>  
  
-   <span data-ttu-id="65f0d-143">管理者が一連の権限をコードのグループ (コード グループ) で関連付けることにより、セキュリティ ポリシーを構成できるようにする。</span><span class="sxs-lookup"><span data-stu-id="65f0d-143">Enables administrators to configure security policy by associating sets of permissions with groups of code (code groups).</span></span>  
  
-   <span data-ttu-id="65f0d-144">実行に不可欠な権限のほか、あった方がよいと思われる権限、決して与えてはならない権限をコードから要求できるようにする。</span><span class="sxs-lookup"><span data-stu-id="65f0d-144">Enables code to request the permissions it requires in order to run, as well as the permissions that would be useful to have, and specifies which permissions the code must never have.</span></span>  
  
-   <span data-ttu-id="65f0d-145">コードによって要求された権限およびセキュリティ ポリシーによって許可された操作に基づいて、読み込まれた各アセンブリに権限を付与する。</span><span class="sxs-lookup"><span data-stu-id="65f0d-145">Grants permissions to each assembly that is loaded, based on the permissions requested by the code and on the operations permitted by security policy.</span></span>  
  
-   <span data-ttu-id="65f0d-146">呼び出し元が特定の権限を所有していることをコードから要求できるようにする。</span><span class="sxs-lookup"><span data-stu-id="65f0d-146">Enables code to demand that its callers have specific permissions.</span></span>  
  
-   <span data-ttu-id="65f0d-147">呼び出し元にデジタル署名があることをコード自身が要求できるようにします。これにより、特定の組織またはサイトからの呼び出し元だけが、保護されたコードを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-147">Enables code to demand that its callers possess a digital signature, thus allowing only callers from a particular organization or site to call the protected code.</span></span>  
  
-   <span data-ttu-id="65f0d-148">呼び出し履歴上で、各呼び出し元に付与された権限を、その呼び出し元に求められる権限と比較することにより、コードに対する制限を実行時に強制する。</span><span class="sxs-lookup"><span data-stu-id="65f0d-148">Enforces restrictions on code at run time by comparing the granted permissions of every caller on the call stack to the permissions that callers must have.</span></span>  
  
 <span data-ttu-id="65f0d-149">攻撃を許した場合でも損害の規模を最小限に抑えるため、コードのセキュリティ コンテキストを選択し、コードの処理に必要なリソースへの権限だけを付与し、それ以外は実行できないようにする。</span><span class="sxs-lookup"><span data-stu-id="65f0d-149">To minimize the amount of damage that can occur if an attack succeeds, choose a security context for your code that grants access only to the resources it needs to get its work done and no more.</span></span>  
  
 <span data-ttu-id="65f0d-150">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f0d-150">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="65f0d-151">リソース</span><span class="sxs-lookup"><span data-stu-id="65f0d-151">Resource</span></span>|<span data-ttu-id="65f0d-152">説明</span><span class="sxs-lookup"><span data-stu-id="65f0d-152">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="65f0d-153">コード アクセス セキュリティと ADO.NET</span><span class="sxs-lookup"><span data-stu-id="65f0d-153">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)|<span data-ttu-id="65f0d-154">ADO.NET アプリケーションの観点から、コード アクセス セキュリティ、ロール ベース セキュリティ、および部分信頼環境間の相互作用について説明します。</span><span class="sxs-lookup"><span data-stu-id="65f0d-154">Describes the interactions between code access security, role-based security, and partially trusted environments from the perspective of an ADO.NET application.</span></span>|  
|[<span data-ttu-id="65f0d-155">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="65f0d-155">Code Access Security</span></span>](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|<span data-ttu-id="65f0d-156">.NET Framework の CAS について説明する追加のトピックへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="65f0d-156">Contains links to additional topics describing CAS in the .NET Framework.</span></span>|  
  
## <a name="database-security"></a><span data-ttu-id="65f0d-157">データベース セキュリティ</span><span class="sxs-lookup"><span data-stu-id="65f0d-157">Database Security</span></span>  
 <span data-ttu-id="65f0d-158">最小特権の原則はデータ ソースにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="65f0d-158">The principle of least privilege also applies to your data source.</span></span> <span data-ttu-id="65f0d-159">データベース セキュリティの一般的なガイドラインは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="65f0d-159">Some general guidelines for database security include:</span></span>  
  
-   <span data-ttu-id="65f0d-160">アカウントをできるだけ低い権限で作成する。</span><span class="sxs-lookup"><span data-stu-id="65f0d-160">Create accounts with the lowest possible privileges.</span></span>  
  
-   <span data-ttu-id="65f0d-161">単にコードの正常動作を目的としてユーザーに管理者アカウントにアクセスさせることは避ける。</span><span class="sxs-lookup"><span data-stu-id="65f0d-161">Do not allow users access to administrative accounts just to get code working.</span></span>  
  
-   <span data-ttu-id="65f0d-162">サーバー側のエラー メッセージをクライアント アプリケーションに返さない。</span><span class="sxs-lookup"><span data-stu-id="65f0d-162">Do not return server-side error messages to client applications.</span></span>  
  
-   <span data-ttu-id="65f0d-163">クライアントとサーバーの両方ですべての入力を検証する。</span><span class="sxs-lookup"><span data-stu-id="65f0d-163">Validate all input at both the client and the server.</span></span>  
  
-   <span data-ttu-id="65f0d-164">動的 SQL ステートメントは避け、パラメーター化コマンドを使用するようにする。</span><span class="sxs-lookup"><span data-stu-id="65f0d-164">Use parameterized commands and avoid dynamic SQL statements.</span></span>  
  
-   <span data-ttu-id="65f0d-165">データベースのセキュリティ監査とログ記録を有効にし、セキュリティ侵害が発生した場合に警告を受けることができるようにする。</span><span class="sxs-lookup"><span data-stu-id="65f0d-165">Enable security auditing and logging for the database you are using so that you are alerted to any security breaches.</span></span>  
  
 <span data-ttu-id="65f0d-166">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f0d-166">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="65f0d-167">リソース</span><span class="sxs-lookup"><span data-stu-id="65f0d-167">Resource</span></span>|<span data-ttu-id="65f0d-168">説明</span><span class="sxs-lookup"><span data-stu-id="65f0d-168">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="65f0d-169">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="65f0d-169">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)|<span data-ttu-id="65f0d-170">SQL Server のセキュリティの概要を説明します。アプリケーションのシナリオを交えながら、SQL Server を対象とした安全な ADO.NET アプリケーションを作成するための指針を提供します。</span><span class="sxs-lookup"><span data-stu-id="65f0d-170">Provides an overview of SQL Server security with application scenarios that provide guidance for creating secure ADO.NET applications that target SQL Server.</span></span>|  
|[<span data-ttu-id="65f0d-171">データ アクセスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="65f0d-171">Recommendations for Data Access Strategies</span></span>](http://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)|<span data-ttu-id="65f0d-172">データへのアクセスおよびデータベース操作の実行に関連した推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="65f0d-172">Provides recommendations for accessing data and performing database operations.</span></span>|  
  
## <a name="security-policy-and-administration"></a><span data-ttu-id="65f0d-173">セキュリティ ポリシーと管理</span><span class="sxs-lookup"><span data-stu-id="65f0d-173">Security Policy and Administration</span></span>  
 <span data-ttu-id="65f0d-174">コード アクセス セキュリティ (CAS) ポリシーの管理が不適切だと、セキュリティの脆弱性を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-174">Improperly administering code access security (CAS) policy can potentially create security weaknesses.</span></span> <span data-ttu-id="65f0d-175">アプリケーションを展開した後は、セキュリティ監視技法を適用し、新しい脅威が現れた際はそのリスクを評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f0d-175">Once an application is deployed, techniques for monitoring security should be used and risks evaluated as new threats emerge.</span></span>  
  
 <span data-ttu-id="65f0d-176">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f0d-176">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="65f0d-177">リソース</span><span class="sxs-lookup"><span data-stu-id="65f0d-177">Resource</span></span>|<span data-ttu-id="65f0d-178">説明</span><span class="sxs-lookup"><span data-stu-id="65f0d-178">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="65f0d-179">NIB: セキュリティ ポリシーの管理</span><span class="sxs-lookup"><span data-stu-id="65f0d-179">NIB: Security Policy Management</span></span>](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)|<span data-ttu-id="65f0d-180">セキュリティ ポリシーの作成と管理について説明します。</span><span class="sxs-lookup"><span data-stu-id="65f0d-180">Provides information on creating and administering security policy.</span></span>|  
|[<span data-ttu-id="65f0d-181">NIB: セキュリティ ポリシーのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="65f0d-181">NIB: Security Policy Best Practices</span></span>](http://msdn.microsoft.com/library/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05)|<span data-ttu-id="65f0d-182">セキュリティ ポリシーの管理方法について説明したトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="65f0d-182">Provides links describing how to administer security policy.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65f0d-183">参照</span><span class="sxs-lookup"><span data-stu-id="65f0d-183">See Also</span></span>  
 [<span data-ttu-id="65f0d-184">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="65f0d-184">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="65f0d-185">ネイティブ コードと .NET Framework コードのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="65f0d-185">PAVE Security in Native and .NET Framework Code</span></span>](http://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [<span data-ttu-id="65f0d-186">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="65f0d-186">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [<span data-ttu-id="65f0d-187">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="65f0d-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
