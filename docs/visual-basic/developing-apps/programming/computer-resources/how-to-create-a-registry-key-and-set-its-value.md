---
title: "方法: レジストリ キーを作成し、その値を設定する (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
dev_langs:
- VB
helpviewer_keywords:
- registry keys, creating
- registry, adding values
- registry, adding keys
- registry keys, setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: 30
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
ms.openlocfilehash: 106a98a1b15c37eb2cac05e1a681bf7dfed3543d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="13130-102">方法: レジストリ キーを作成し、その値を設定する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13130-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="13130-103">レジストリ キーを作成するには、`My.Computer.Registry` オブジェクトの `CreateSubKey` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="13130-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="13130-104">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="13130-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="13130-105">レジストリ キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="13130-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="13130-106">`CreateSubKey` メソッドを使用し、キーを入れるハイブとキー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="13130-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="13130-107">パラメーター `Subkey` では、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="13130-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="13130-108">この例では、HKEY_CURRENT_USER の下にレジストリ キー `MyTestKey` を作成します。</span><span class="sxs-lookup"><span data-stu-id="13130-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     <span data-ttu-id="13130-109">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="13130-109">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span></span>  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="13130-110">レジストリ キーを作成し、それに値を設定するには</span><span class="sxs-lookup"><span data-stu-id="13130-110">To create a registry key and set a value in it</span></span>  
  
1.  <span data-ttu-id="13130-111">`CreateSubkey` メソッドを使用し、キーを入れるハイブとキー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="13130-111">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="13130-112">この例では、HKEY_CURRENT_USER の下にレジストリ キー `MyTestKey` を作成します。</span><span class="sxs-lookup"><span data-stu-id="13130-112">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     <span data-ttu-id="13130-113">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="13130-113">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span></span>  
  
2.  <span data-ttu-id="13130-114">値は、`SetValue` メソッドを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="13130-114">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="13130-115">この例では、文字列値</span><span class="sxs-lookup"><span data-stu-id="13130-115">This example sets the string value.</span></span> <span data-ttu-id="13130-116">"MyTestKeyValue" を "This is a test value" に設定します。</span><span class="sxs-lookup"><span data-stu-id="13130-116">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     <span data-ttu-id="13130-117">[!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="13130-117">[!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="13130-118">例</span><span class="sxs-lookup"><span data-stu-id="13130-118">Example</span></span>  
 <span data-ttu-id="13130-119">この例では、HKEY_CURRENT_USER の下にレジストリ キー `MyTestKey` を作成し、文字列値 `MyTestKeyValue` を `This is a test value` に設定します。</span><span class="sxs-lookup"><span data-stu-id="13130-119">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 <span data-ttu-id="13130-120">[!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="13130-120">[!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="13130-121">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="13130-121">Robust Programming</span></span>  
 <span data-ttu-id="13130-122">レジストリの構造を調べて、キーの適切な場所を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="13130-122">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="13130-123">たとえば、現在のユーザーの HKEY_CURRENT_USER\Software キーを開き、会社名のキーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="13130-123">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="13130-124">その後で、会社名のキーにレジストリ値を追加します。</span><span class="sxs-lookup"><span data-stu-id="13130-124">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="13130-125">Web アプリケーションからレジストリを読み取る際、現在のユーザーは Web アプリケーションに実装されている認証と偽装によります。</span><span class="sxs-lookup"><span data-stu-id="13130-125">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="13130-126">ローカル コンピューター (<xref:Microsoft.Win32.Registry.LocalMachine>) よりもユーザー フォルダー (<xref:Microsoft.Win32.Registry.CurrentUser>) にデータを書き込む方が安全です。</span><span class="sxs-lookup"><span data-stu-id="13130-126">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="13130-127">レジストリの値を作成するときは、その値が既存の値である場合の処理を決めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="13130-127">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="13130-128">悪意のあるユーザーによって作成された別のプロセスが既に値を作成し、アクセス権を持っている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13130-128">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="13130-129">レジストリ値にデータを設定すると、そのデータを他のプロセスから利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="13130-129">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="13130-130">これを回避するには、<xref:Microsoft.Win32.RegistryKey.GetValue%2A> メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="13130-130">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="13130-131">このメソッドは、キーがまだ存在しない場合、`Nothing` を返します。</span><span class="sxs-lookup"><span data-stu-id="13130-131">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="13130-132">レジストリ キーがアクセス制御リスト (ACL: Access Control List) によって保護されていても、パスワードなど他人に知られたくないデータをプレーン テキストでレジストリに格納するのは危険です。</span><span class="sxs-lookup"><span data-stu-id="13130-132">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="13130-133">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13130-133">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="13130-134">キーの名前が `Nothing` である場合 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="13130-134">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="13130-135">レジストリ キーを作成するためのアクセス許可がユーザーにない場合 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="13130-135">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="13130-136">キー名が 255 文字の制限を超えている場合 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="13130-136">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="13130-137">キーが閉じている場合 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="13130-137">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="13130-138">レジストリ キーが読み取り専用の場合 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="13130-138">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="13130-139">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="13130-139">.NET Framework Security</span></span>  
 <span data-ttu-id="13130-140">このプロセスを実行するには、アセンブリに対して <xref:System.Security.Permissions.RegistryPermission> クラスで特権レベルが許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="13130-140">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="13130-141">部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないために例外をスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13130-141">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="13130-142">同様に、ユーザーには、設定に対する作成や書き込みを行うための適切な ACL が必要です。</span><span class="sxs-lookup"><span data-stu-id="13130-142">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="13130-143">たとえば、コード アクセス セキュリティのアクセス許可を持つローカル アプリケーションには、オペレーティング システムのアクセス許可がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13130-143">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="13130-144">詳しくは、「[コード アクセス セキュリティの基礎](https://msdn.microsoft.com/library/33tceax8)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="13130-144">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13130-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="13130-145">See Also</span></span>  
 <span data-ttu-id="13130-146"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy></span><span class="sxs-lookup"><span data-stu-id="13130-146"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy></span></span>   
 <span data-ttu-id="13130-147"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A></span><span class="sxs-lookup"><span data-stu-id="13130-147"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A></span></span>   
 <span data-ttu-id="13130-148"><xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="13130-148"><xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A></span></span>   
 <span data-ttu-id="13130-149">[レジストリからの読み取りとレジストリへの書き込み](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="13130-149">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
 [<span data-ttu-id="13130-150">コード アクセス セキュリティの基礎</span><span class="sxs-lookup"><span data-stu-id="13130-150">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)

