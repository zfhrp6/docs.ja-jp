---
title: "方法: レジストリにキーを作成する (Visual C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 96d34df3314494fc96ad8b55d7462b67dcc7bd72
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="d9566-102">方法: レジストリにキーを作成する (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="d9566-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="d9566-103">現在のユーザーのレジストリに存在する "Names" というキーの下に "Name" と "Isabella" という値のペアを追加する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d9566-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9566-104">例</span><span class="sxs-lookup"><span data-stu-id="d9566-104">Example</span></span>  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d9566-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d9566-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d9566-106">コードをコピーし、コンソール アプリケーションの `Main` メソッドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d9566-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="d9566-107">`Names` パラメーターをレジストリの HKEY_CURRENT_USER ノードの直下にあるキーの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d9566-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="d9566-108">`Name` パラメーターを Names ノードの直下にある値の名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d9566-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d9566-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="d9566-109">Robust Programming</span></span>  
 <span data-ttu-id="d9566-110">レジストリの構造を調べて、キーの適切な場所を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="d9566-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="d9566-111">たとえば、現在のユーザーの Software キーを開き、会社名のキーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d9566-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="d9566-112">その後で、会社名のキーにレジストリ値を追加します。</span><span class="sxs-lookup"><span data-stu-id="d9566-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="d9566-113">次の条件では例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d9566-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="d9566-114">キーの名前が null である場合。</span><span class="sxs-lookup"><span data-stu-id="d9566-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="d9566-115">レジストリ キーを作成するためのアクセス許可がユーザーにない場合。</span><span class="sxs-lookup"><span data-stu-id="d9566-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="d9566-116">キー名が 255 文字の制限を超えている場合。</span><span class="sxs-lookup"><span data-stu-id="d9566-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="d9566-117">キーが閉じている場合。</span><span class="sxs-lookup"><span data-stu-id="d9566-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="d9566-118">レジストリ キーが読み取り専用の場合。</span><span class="sxs-lookup"><span data-stu-id="d9566-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d9566-119">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d9566-119">.NET Framework Security</span></span>  
 <span data-ttu-id="d9566-120">ローカル コンピューター (`Microsoft.Win32.Registry.CurrentUser`) よりもユーザー フォルダー (`Microsoft.Win32.Registry.LocalMachine`) にデータを書き込む方が安全です。</span><span class="sxs-lookup"><span data-stu-id="d9566-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="d9566-121">レジストリの値を作成するときは、その値が既存の値である場合の処理を決めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9566-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="d9566-122">悪意のあるユーザーによって作成された別のプロセスが既に値を作成し、アクセス権を持っている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d9566-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="d9566-123">レジストリ値にデータを設定すると、そのデータを他のプロセスから利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d9566-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="d9566-124">これを回避するには、`Overload:Microsoft.Win32.RegistryKey.GetValue` </span><span class="sxs-lookup"><span data-stu-id="d9566-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="d9566-125">メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="d9566-125">method.</span></span> <span data-ttu-id="d9566-126">このメソッドは、キーがまだ存在しない場合、null を返します。</span><span class="sxs-lookup"><span data-stu-id="d9566-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="d9566-127">レジストリ キーがアクセス制御リスト (ACL: Access Control List) によって保護されていても、パスワードなど他人に知られたくないデータをプレーン テキストでレジストリに格納するのは危険です。</span><span class="sxs-lookup"><span data-stu-id="d9566-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9566-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9566-128">See Also</span></span>  
 <span data-ttu-id="d9566-129"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d9566-129"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="d9566-130">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d9566-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d9566-131">[ファイル システムとレジストリ (C# プログラミング ガイド)](../../../csharp/programming-guide/file-system/index.md) </span><span class="sxs-lookup"><span data-stu-id="d9566-131">[File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md) </span></span>  
 [<span data-ttu-id="d9566-132">C# によるレジストリからの読み取り、書き込み、および削除</span><span class="sxs-lookup"><span data-stu-id="d9566-132">Read, write and delete from the registry with C#</span></span>](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)

