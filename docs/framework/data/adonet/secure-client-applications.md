---
title: "安全なクライアント アプリケーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1218cda46a6a901c3dbf9fb11333b04d0133df42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="secure-client-applications"></a><span data-ttu-id="4e106-102">安全なクライアント アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4e106-102">Secure Client Applications</span></span>
<span data-ttu-id="4e106-103">通常、アプリケーションは多数の要素で構成されており、それぞれをデータの損失やシステムのセキュリティ侵害を招く脆弱性から確実に保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e106-103">Applications typically consist of many parts that must all be protected from vulnerabilities that could result in data loss or otherwise compromise the system.</span></span> <span data-ttu-id="4e106-104">安全なユーザー インターフェイスを作成し、攻撃者によるデータやシステム リソースへのアクセスを未然に阻止することで、多くの問題を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="4e106-104">Creating secure user interfaces can prevent many problems by blocking attackers before they can access data or system resources.</span></span>  
  
## <a name="validate-user-input"></a><span data-ttu-id="4e106-105">ユーザー入力の検証</span><span class="sxs-lookup"><span data-stu-id="4e106-105">Validate User Input</span></span>  
 <span data-ttu-id="4e106-106">データにアクセスするアプリケーションを構築する場合、ユーザーの入力はすべて悪意のあるものと想定しない限り、</span><span class="sxs-lookup"><span data-stu-id="4e106-106">When constructing an application that accesses data, you should assume that all user input is malicious until proven otherwise.</span></span> <span data-ttu-id="4e106-107">攻撃に対する脆弱性をアプリケーションから取り除くことはできません。</span><span class="sxs-lookup"><span data-stu-id="4e106-107">Failure to do so can leave your application vulnerable to attack.</span></span> <span data-ttu-id="4e106-108">.NET Framework には、入力できる文字数の制限など、入力コントロールの値の範囲を設定するクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4e106-108">The .NET Framework contains classes to help you enforce a domain of values for input controls, such as limiting the number of characters that can be entered.</span></span> <span data-ttu-id="4e106-109">イベントを捕捉することによって、値の有効性を確認するプロシージャを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4e106-109">Event hooks allow you to write procedures to check the validity of values.</span></span> <span data-ttu-id="4e106-110">ユーザーによって入力されるデータを検証し、厳密に型指定することで、アプリケーションをスクリプト インジェクションや SQL インジェクションなどの攻撃にさらす機会を制限できます。</span><span class="sxs-lookup"><span data-stu-id="4e106-110">User input data can be validated and strongly typed, limiting an application's exposure to script and SQL injection exploits.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e106-111">クライアント アプリケーションだけでなく、データ ソース側でもユーザー入力を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e106-111">You must also validate user input at the data source as well as in the client application.</span></span> <span data-ttu-id="4e106-112">攻撃者がアプリケーションを迂回し、データ ソースを直接攻撃してくる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="4e106-112">An attacker may choose to circumvent your application and attack the data source directly.</span></span>  
  
 [<span data-ttu-id="4e106-113">セキュリティとユーザー入力</span><span class="sxs-lookup"><span data-stu-id="4e106-113">Security and User Input</span></span>](../../../../docs/standard/security/security-and-user-input.md)  
 <span data-ttu-id="4e106-114">発見が難しく大きな危険を招く可能性のあるユーザー入力に関連したバグへの対処方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-114">Describes how to handle subtle and potentially dangerous bugs involving user input.</span></span>  
  
 [<span data-ttu-id="4e106-115">ASP.NET Web ページで、ユーザー入力の検証</span><span class="sxs-lookup"><span data-stu-id="4e106-115">Validating User Input in ASP.NET Web Pages</span></span>](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 <span data-ttu-id="4e106-116">ASP.NET の検証コントロールを使ったユーザー入力の検証について概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-116">Overview of validating user input using ASP.NET validation controls.</span></span>  
  
 [<span data-ttu-id="4e106-117">Windows フォームでのユーザー入力</span><span class="sxs-lookup"><span data-stu-id="4e106-117">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 <span data-ttu-id="4e106-118">Windows フォーム アプリケーションにおけるマウス入力およびキーボード入力の検証に関連したリンクや情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4e106-118">Provides links and information for validating mouse and keyboard input in a Windows Forms application.</span></span>  
  
 [<span data-ttu-id="4e106-119">.NET Framework 正規表現</span><span class="sxs-lookup"><span data-stu-id="4e106-119">.NET Framework Regular Expressions</span></span>](../../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="4e106-120"><xref:System.Text.RegularExpressions.Regex> クラスを使用してユーザー入力の有効性を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-120">Describes how to use the <xref:System.Text.RegularExpressions.Regex> class to check the validity of user input.</span></span>  
  
## <a name="windows-applications"></a><span data-ttu-id="4e106-121">Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4e106-121">Windows Applications</span></span>  
 <span data-ttu-id="4e106-122">これまで、Windows アプリケーションは、アクセスがすべて許可された状態で実行されていました。</span><span class="sxs-lookup"><span data-stu-id="4e106-122">In the past, Windows applications generally ran with full permissions.</span></span> <span data-ttu-id="4e106-123">.NET Framework は、コード アクセス セキュリティ (CAS) を使用して Windows アプリケーションで実行されるコードを制限するインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="4e106-123">The .NET Framework provides the infrastructure to restrict code executing in a Windows application by using code access security (CAS).</span></span> <span data-ttu-id="4e106-124">ただし、CAS だけでは、アプリケーションを保護するには不十分です。</span><span class="sxs-lookup"><span data-stu-id="4e106-124">However, CAS alone is not enough to protect your application.</span></span>  
  
 [<span data-ttu-id="4e106-125">Windows フォームのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="4e106-125">Windows Forms Security</span></span>](../../../../docs/framework/winforms/windows-forms-security.md)  
 <span data-ttu-id="4e106-126">Windows フォーム アプリケーションをセキュリティで保護する方法について説明します。また、関連項目へのリンクがあります。</span><span class="sxs-lookup"><span data-stu-id="4e106-126">Discusses how to secure Windows Forms applications and provides links to related topics.</span></span>  
  
 [<span data-ttu-id="4e106-127">Windows フォームとアンマネージ アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4e106-127">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 <span data-ttu-id="4e106-128">Windows フォーム アプリケーションでアンマネージ アプリケーションと対話する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-128">Describes how to interact with unmanaged applications in a Windows Forms application.</span></span>  
  
 [<span data-ttu-id="4e106-129">ClickOnce 配置の Windows フォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4e106-129">ClickOnce Deployment for Windows Forms Applications</span></span>](http://msdn.microsoft.com/en-us/34d8c770-48f2-460c-8d67-4ea5684511df)  
 <span data-ttu-id="4e106-130">Windows フォーム アプリケーションでの `ClickOnce` 配置の使用方法およびセキュリティへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-130">Describes how to use `ClickOnce` deployment in a Windows Forms application and discusses the security implications.</span></span>  
  
## <a name="aspnet-and-xml-web-services"></a><span data-ttu-id="4e106-131">ASP.NET と XML Web サービス</span><span class="sxs-lookup"><span data-stu-id="4e106-131">ASP.NET and XML Web Services</span></span>  
 <span data-ttu-id="4e106-132">通常、ASP.NET アプリケーションは、アクセスを Web サイトの一部に制限し、データ保護およびサイト セキュリティのための他のメカニズムを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e106-132">ASP.NET applications generally need to restrict access to some portions of the Web site and provide other mechanisms for data protection and site security.</span></span> <span data-ttu-id="4e106-133">以下のリンクにアクセスすると、ASP.NET アプリケーションをセキュリティで保護するための有益な情報を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="4e106-133">These links provide useful information for securing your ASP.NET application.</span></span>  
  
 <span data-ttu-id="4e106-134">XML Web サービスは、ASP.NET アプリケーション、Windows フォーム アプリケーション、またはその他の Web サービスが使用できるデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="4e106-134">An XML Web service provides data that can be consumed by an ASP.NET application, a Windows Forms application, or another Web service.</span></span> <span data-ttu-id="4e106-135">クライアント アプリケーションのセキュリティだけでなく、Web サービスそのもののセキュリティを管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e106-135">You need to manage security for the Web service itself as well as security for the client application.</span></span>  
  
 <span data-ttu-id="4e106-136">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e106-136">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="4e106-137">リソース</span><span class="sxs-lookup"><span data-stu-id="4e106-137">Resource</span></span>|<span data-ttu-id="4e106-138">説明</span><span class="sxs-lookup"><span data-stu-id="4e106-138">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="4e106-139">NIB: ASP.NET のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="4e106-139">NIB: ASP.NET Security</span></span>](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d)|<span data-ttu-id="4e106-140">ASP.NET アプリケーションをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-140">Discusses how to secure ASP.NET applications.</span></span>|  
|[<span data-ttu-id="4e106-141">ASP.NET を使用して作成された XML Web サービスをセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="4e106-141">Securing XML Web Services Created Using ASP.NET</span></span>](http://msdn.microsoft.com/en-us/354b2ab1-2782-4542-b32a-dc560178b90c)|<span data-ttu-id="4e106-142">ASP.NET Web サービスへのセキュリティの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-142">Discusses how to implement security for an ASP.NET Web Service.</span></span>|  
|[<span data-ttu-id="4e106-143">スクリプトによる攻略の概要</span><span class="sxs-lookup"><span data-stu-id="4e106-143">Script Exploits Overview</span></span>](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|<span data-ttu-id="4e106-144">Web ページに悪意のある文字の挿入を試みるスクリプト攻略攻撃を阻止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-144">Discusses how to guard against a script exploit attack, which attempts to insert malicious characters into a Web page.</span></span>|  
|[<span data-ttu-id="4e106-145">NIB: Basic ASP.NET Web アプリケーションのセキュリティのプラクティス</span><span class="sxs-lookup"><span data-stu-id="4e106-145">NIB:Basic Security Practices for ASP.NET Web Applications</span></span>](http://msdn.microsoft.com/en-us/94a52ab8-731d-417e-b997-721baf43df38)|<span data-ttu-id="4e106-146">一般的なセキュリティ情報のほか、より詳細なページへのリンクも掲載されています。</span><span class="sxs-lookup"><span data-stu-id="4e106-146">General security information and links to further discussion,</span></span>|  
  
## <a name="remoting"></a><span data-ttu-id="4e106-147">リモート処理</span><span class="sxs-lookup"><span data-stu-id="4e106-147">Remoting</span></span>  
 <span data-ttu-id="4e106-148">.NET リモート処理を使用すると、広範囲の分散アプリケーションを簡単に構築できます。その場合、アプリケーションのコンポーネントを、すべて 1 台のコンピューターに置くことも、遠隔地のコンピューターに分散させることもできます。</span><span class="sxs-lookup"><span data-stu-id="4e106-148">.NET remoting enables you to build widely distributed applications easily, whether the application components are all on one computer or spread out across the entire world.</span></span> <span data-ttu-id="4e106-149">同じコンピューター上、またはネットワークを経由してアクセスできる他の任意のコンピューター上にある他のプロセスのオブジェクトを使用するクライアント アプリケーションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="4e106-149">You can build client applications that use objects in other processes on the same computer or on any other computer that is reachable over its network.</span></span> <span data-ttu-id="4e106-150">また、.NET リモート処理を使用すると、同じプロセスの他のアプリケーション ドメインと通信できます。</span><span class="sxs-lookup"><span data-stu-id="4e106-150">You can also use .NET remoting to communicate with other application domains in the same process.</span></span>  
  
|<span data-ttu-id="4e106-151">リソース</span><span class="sxs-lookup"><span data-stu-id="4e106-151">Resource</span></span>|<span data-ttu-id="4e106-152">説明</span><span class="sxs-lookup"><span data-stu-id="4e106-152">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="4e106-153">リモート アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="4e106-153">Configuration of Remote Applications</span></span>](http://msdn.microsoft.com/en-us/92c0c097-d984-4315-835b-7490ecdf1097)|<span data-ttu-id="4e106-154">一般的な問題を回避するためのリモート処理アプリケーションの構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-154">Discusses how to configure remoting applications in order to avoid common problems.</span></span>|  
|[<span data-ttu-id="4e106-155">リモート処理でのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="4e106-155">Security in Remoting</span></span>](http://msdn.microsoft.com/en-us/9574262c-d4b1-41c5-8600-24ff147c0add)|<span data-ttu-id="4e106-156">認証と暗号化のほか、リモート処理に関連したその他のセキュリティ トピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-156">Describes authentication and encryption as well as additional security topics relevant to remoting.</span></span>|  
|[<span data-ttu-id="4e106-157">セキュリティとリモート処理の考慮事項</span><span class="sxs-lookup"><span data-stu-id="4e106-157">Security and Remoting Considerations</span></span>](../../../../docs/framework/misc/security-and-remoting-considerations.md)|<span data-ttu-id="4e106-158">保護されたオブジェクトやアプリケーション ドメインの境界越えに伴うセキュリティの問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e106-158">Describes security issues with protected objects and application domain crossing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e106-159">参照</span><span class="sxs-lookup"><span data-stu-id="4e106-159">See Also</span></span>  
 [<span data-ttu-id="4e106-160">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="4e106-160">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="4e106-161">データ アクセスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="4e106-161">Recommendations for Data Access Strategies</span></span>](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [<span data-ttu-id="4e106-162">アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="4e106-162">Securing Applications</span></span>](/visualstudio/ide/securing-applications)  
 [<span data-ttu-id="4e106-163">接続情報の保護</span><span class="sxs-lookup"><span data-stu-id="4e106-163">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [<span data-ttu-id="4e106-164">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="4e106-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
