---
title: "Assert メソッドの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e5d910e0d6e6f55234255ac378fa58ebf7f307
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-assert-method"></a><span data-ttu-id="e0b50-102">Assert メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="e0b50-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="e0b50-103"><xref:System.Security.CodeAccessPermission.Assert%2A> は、コードのアクセス許可のクラスおよび <xref:System.Security.PermissionSet>クラスで呼び出すことができるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="e0b50-104">使用することができます**Assert**コードが権限を持つ操作が呼び出し元を実行する、コード (および下流の呼び出し元) を有効にする権限がないためにします。</span><span class="sxs-lookup"><span data-stu-id="e0b50-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="e0b50-105">セキュリティ アサーションは、セキュリティ チェック時にランタイムが実行する正常なプロセスを変更します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="e0b50-106">アクセス許可をアサートすると、アサートされたアクセス許可のためにコードの呼び出し元をチェックしないようセキュリティ システムに指示します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e0b50-107">アサーションはセキュリティ ホールを開き、セキュリティの制限事項を適用するランタイムのメカニズムを弱体化させる可能性があるため、慎重に使用してください。</span><span class="sxs-lookup"><span data-stu-id="e0b50-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="e0b50-108">アサーションは、ライブラリがアンマネージ コードを呼び出す状況、またはライブラリの使用目的と明らかに関係のないアクセス許可を必要とする呼び出しを行う状況に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e0b50-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="e0b50-109">たとえば、すべてのマネージ コードのあるアンマネージ コードを呼び出す必要があります**SecurityPermission**で、 **UnmanagedCode**フラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="e0b50-110">ローカルのイントラネットからダウンロードするコードなど、ローカル コンピューターから発生していないコードには、既定でこのアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="e0b50-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="e0b50-111">そのため、ローカルのイントラネットからダウンロードするコードがアンマネージ コードを使用するライブラリを呼び出せるようにするには、ライブラリによってアサートされたアクセス許可がコードに指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b50-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="e0b50-112">さらに、ライブラリによっては呼び出し元からは見えない呼び出し、および特別なアクセス許可を必要とする呼び出しを行う場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0b50-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="e0b50-113">また、コードが呼び出し元から完全に非表示にされる方法でリソースにアクセスする状況において、アサーションを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e0b50-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="e0b50-114">たとえば、ライブラリがデータベースから情報を取得しますが、プロセス内でコンピューターのレジストリからも情報を読み取ると仮定してください。</span><span class="sxs-lookup"><span data-stu-id="e0b50-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="e0b50-115">ライブラリを使用している開発者はアクセスできないため、ソースに、あるありません、コードが必要であるかを知る方法**RegistryPermission**のコードを使用するためにします。</span><span class="sxs-lookup"><span data-stu-id="e0b50-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="e0b50-116">この場合、コードの呼び出し元がレジストリへのアクセス許可を持つことを求めるのは妥当でないか不必要と判断した場合は、レジストリを読み取るアクセス許可をアサートすることができます。</span><span class="sxs-lookup"><span data-stu-id="e0b50-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="e0b50-117">このような状況であることがなく呼び出し元のため、アクセス許可をアサートするライブラリの適切な**RegistryPermission**ライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e0b50-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="e0b50-118">アサーションがスタック ウォークに影響を与えるのは、アサートされたアクセス許可および下流の呼び出し元によって要求されるアクセス許可が同じ型である場合、かつ要求されたアクセス許可がアサートされているアクセス許可のサブセットである場合のみです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="e0b50-119">たとえば、アサートする**FileIOPermission**に対して C ドライブとダウン ストリームの要求時にすべてのファイルを読み取ることが行われた**FileIOPermission** C:\Temp 内のファイルを読み取り、アサーションに影響を与える、スタック ウォーク;ただし、要求の対象場合**FileIOPermission** C ドライブに書き込むアサーション効果はありません。</span><span class="sxs-lookup"><span data-stu-id="e0b50-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="e0b50-120">アサーションを実行する場合、コードにアサートしているアクセス許可と、アサーションを実行する権利を表す <xref:System.Security.Permissions.SecurityPermission> の両方が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b50-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="e0b50-121">コードに付与されていないアクセス許可をアサートすることができますが、アサーションがセキュリティ チェックを成功させようとする前にセキュリティ チェックが失敗するため、アサーションが無意味になってしまいます。</span><span class="sxs-lookup"><span data-stu-id="e0b50-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="e0b50-122">次の図を使用するときに起こる**Assert**です。</span><span class="sxs-lookup"><span data-stu-id="e0b50-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="e0b50-123">次のステートメントについて、アセンブリ A、B、C、E、および F が true であり、P1 と P1A という 2 つのアクセス許可があると仮定してください。</span><span class="sxs-lookup"><span data-stu-id="e0b50-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
-   <span data-ttu-id="e0b50-124">P1A は C ドライブ上の .txt ファイルを読み取る権限を表します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
-   <span data-ttu-id="e0b50-125">P1 は C ドライブ上のすべてのファイルを読み取る権限を表します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-125">P1 represents the right to read all files on the C drive.</span></span>  
  
-   <span data-ttu-id="e0b50-126">P1A と P1 の両方が**FileIOPermission**型、および P1A は P1 のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
-   <span data-ttu-id="e0b50-127">アセンブリ E と F には P1A のアクセス許可が付与されています。</span><span class="sxs-lookup"><span data-stu-id="e0b50-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
-   <span data-ttu-id="e0b50-128">アセンブリ C には P1 のアクセス許可が付与されています。</span><span class="sxs-lookup"><span data-stu-id="e0b50-128">Assembly C has been granted P1 permission.</span></span>  
  
-   <span data-ttu-id="e0b50-129">アセンブリ A と B には P1 と P1A のアクセス許可のいずれも付与されていません。</span><span class="sxs-lookup"><span data-stu-id="e0b50-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
-   <span data-ttu-id="e0b50-130">メソッド A はアセンブリ A 内にあり、メソッド B はアセンブリ B 内にあり、以下同様です。</span><span class="sxs-lookup"><span data-stu-id="e0b50-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 <span data-ttu-id="e0b50-131">![](../../../docs/framework/misc/media/assert.gif "アサート")</span><span class="sxs-lookup"><span data-stu-id="e0b50-131">![](../../../docs/framework/misc/media/assert.gif "assert")</span></span>  
<span data-ttu-id="e0b50-132">Assert の使用</span><span class="sxs-lookup"><span data-stu-id="e0b50-132">Using Assert</span></span>  
  
 <span data-ttu-id="e0b50-133">このシナリオ、メソッド A が B を呼び出し、B が C、E、呼び出し、C および E の呼び出しでは、F. メソッド C は、(アクセス許可の P1)、C ドライブにファイルを読み取る権限と、C ドライブ (P1A のアクセス許可) 上の .txt ファイルを読み取るメソッド E 要求権限をアサートします。</span><span class="sxs-lookup"><span data-stu-id="e0b50-133">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="e0b50-134">F で要求が実行時に発生したときに F のすべての呼び出し元の権限をチェックするスタック ウォークが実行 E から順が与えられて P1A のアクセス、スタック ウォークは処理を C、C のアサーションが検出された場所のアクセス許可を確認するようにします。</span><span class="sxs-lookup"><span data-stu-id="e0b50-134">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="e0b50-135">要求されたアクセス許可 (P1A) は、アサートされたアクセス許可 (P1) のサブセットであるため、スタック ウォークが停止し、セキュリティ チェックは自動的に成功します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-135">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="e0b50-136">アセンブリ A と B に P1A のアクセス許可が付与されていないことは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="e0b50-136">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="e0b50-137">P1 をアサートすることで、メソッド C は、呼び出し元がそのリソースへのアクセス許可を付与されていない場合でも呼び出し元が、P1 で保護されているリソースにアクセスできることを保証します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-137">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="e0b50-138">クラス ライブラリをデザインし、クラスが保護されたリソースにアクセスする場合は、ほとんどの場合、呼び出し元のクラスが適切なアクセス許可を持つことを求めるセキュリティの要求を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b50-138">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="e0b50-139">呼び出すことによって、アクセス許可をアサートするにはこれらの呼び出し元は、コードを呼び出すことができるようにに関する責任を負う許容できる場合とアクセス許可、その呼び出し元のほとんどがわかっている必要がなくクラスは、の操作を実行する場合、 **Assert**コードを実行して、操作を表すためのアクセス許可オブジェクトのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-139">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="e0b50-140">使用して**Assert**を通常そのようにできなかった呼び出し元がこの方法で、コードの呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-140">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="e0b50-141">そのため、アクセス許可をアサートする場合、自分のコンポーネントが誤使用されるのを防ぐために、必ず事前に適切なセキュリティ チェックを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b50-141">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="e0b50-142">たとえば、信頼性の高いライブラリのクラスにファイルを削除するメソッドがあると仮定します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-142">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="e0b50-143">メソッドは、アンマネージ Win32 関数を呼び出してファイルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="e0b50-143">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="e0b50-144">呼び出し元を呼び出すコードの**削除**、削除するファイルの名前を引数としてメソッド C:\Test.txt です。</span><span class="sxs-lookup"><span data-stu-id="e0b50-144">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="e0b50-145">内で、**削除**メソッドは、コードの作成、 <xref:System.Security.Permissions.FileIOPermission> C:\Test.txt への書き込みアクセスを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e0b50-145">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="e0b50-146">(ファイルを削除するには書き込みのアクセス権が必要です。)コードを呼び出します強制セキュリティ チェックを呼び出して、 **FileIOPermission**オブジェクトの**デマンド**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-146">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="e0b50-147">コール スタックのいずれかの呼び出し元にこのアクセス許可がない場合は、<xref:System.Security.SecurityException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e0b50-147">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="e0b50-148">例外がスローされない場合、すべての呼び出し元に C:\Test.txt へのアクセス権があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e0b50-148">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="e0b50-149">呼び出し元のほとんどがアンマネージ コードにアクセスする権限を持っていないことは、コードを作成しと思われるため、<xref:System.Security.Permissions.SecurityPermission>をアンマネージ コードを呼び出す権限を表すオブジェクトを呼び出すオブジェクト**Assert**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-149">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="e0b50-150">最後に、コードは C:\Text.txt を削除するアンマネージ Win32 関数を呼び出し、呼び出し元にコントロールを返します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-150">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e0b50-151">そこで、アサートするためのアクセス許可によって保護されているリソースにアクセスするために自分のコードが他のコードによって使用される状況では、自分のコードでアサーションが使用されていないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b50-151">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="e0b50-152">たとえば、コードでは、パラメーターとして呼び出し元によって名前が指定したファイルに書き込む、アサートしないで、 **FileIOPermission**コードがサード パーティによって悪用されるため、ファイルに書き込むためです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-152">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="e0b50-153">強制セキュリティ構文を使用するときに呼び出す、 **Assert**同じメソッド内で複数のアクセス許可のメソッドがセキュリティ例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e0b50-153">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="e0b50-154">代わりに、作成する必要があります、 **PermissionSet**オブジェクトを呼び出すには、まずする個々 のアクセス許可を渡す、 **Assert**メソッドを**PermissionSet**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e0b50-154">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="e0b50-155">呼び出すことができます、 **Assert**メソッドの宣言セキュリティ構文を使用する場合に 1 回以上です。</span><span class="sxs-lookup"><span data-stu-id="e0b50-155">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="e0b50-156">次の例は、オーバーライド元のセキュリティ チェックの使用に宣言構文を示します、 **Assert**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-156">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="e0b50-157">注意して、 **FileIOPermissionAttribute**構文は次の 2 つの値:<xref:System.Security.Permissions.SecurityAction>列挙型とのファイルまたはディレクトリのアクセス許可が与えられる場所です。</span><span class="sxs-lookup"><span data-stu-id="e0b50-157">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="e0b50-158">呼び出し**Assert**にアクセスするための要求と、`C:\Log.txt`成功した場合でも、呼び出し元は、ファイルへのアクセス権限はチェックされません。</span><span class="sxs-lookup"><span data-stu-id="e0b50-158">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 <span data-ttu-id="e0b50-159">次のコード フラグメントは、オーバーライド元のセキュリティ チェックの使用に強制構文を示します、 **Assert**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0b50-159">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="e0b50-160">この例では、インスタンスでは、 **FileIOPermission**オブジェクトを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e0b50-160">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="e0b50-161">コンス トラクターに渡されます**FileIOPermissionAccess.AllAccess**を許可、アクセスの種類の定義の後にファイルの場所を説明する文字列。</span><span class="sxs-lookup"><span data-stu-id="e0b50-161">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="e0b50-162">1 回、 **FileIOPermission**オブジェクトが定義されている、のみを呼び出す必要があるその**Assert**セキュリティ チェックをオーバーライドするメソッド。</span><span class="sxs-lookup"><span data-stu-id="e0b50-162">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0b50-163">参照</span><span class="sxs-lookup"><span data-stu-id="e0b50-163">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [<span data-ttu-id="e0b50-164">属性</span><span class="sxs-lookup"><span data-stu-id="e0b50-164">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="e0b50-165">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e0b50-165">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
