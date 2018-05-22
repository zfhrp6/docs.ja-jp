---
title: '軽減策: 新しい 64 ビット JIT コンパイラ'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4edce9558cdbdd5937aa12866077210a91ee8494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="4c341-102">軽減策: 新しい 64 ビット JIT コンパイラ</span><span class="sxs-lookup"><span data-stu-id="4c341-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="4c341-103">.NET Framework 4.6 以降では、ランタイムに Just-In-Time コンパイル用の新しい 64 ビット JIT コンパイラが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c341-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="4c341-104">この変更は、32 ビット JIT コンパイラでのコンパイルには影響しません。</span><span class="sxs-lookup"><span data-stu-id="4c341-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="4c341-105">予期しない動作または例外</span><span class="sxs-lookup"><span data-stu-id="4c341-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="4c341-106">場合によっては、新しい 64 ビット JIT コンパイラでのコンパイルの結果、古い 64 ビット JIT コンパイラでコンパイルされたコードの実行時に監視されない動作が発生したり、ランタイム例外が発生したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="4c341-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="4c341-107">既知の相違には次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="4c341-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4c341-108">これらの既知の問題はすべて、.NET Framework 4.6.2 と共にリリースされた新しい 64 ビット コンパイラで対処済みです。</span><span class="sxs-lookup"><span data-stu-id="4c341-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="4c341-109">また、Windows 更新プログラムに含まれる .NET Framework 4.6 および 4.6.1 のサービス リリースでも大部分に対処済みです。</span><span class="sxs-lookup"><span data-stu-id="4c341-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="4c341-110">使用している Windows のバージョンが最新のものであることを確認するか、.NET Framework 4.6.2 にアップグレードすることで、これらの問題を解消できます。</span><span class="sxs-lookup"><span data-stu-id="4c341-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
-   <span data-ttu-id="4c341-111">特定の条件下では、最適化が有効なリリース ビルドの <xref:System.NullReferenceException> がボックス化解除操作でスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4c341-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
-   <span data-ttu-id="4c341-112">場合によっては、大きなメソッド本文の実働コードの実行時に <xref:System.StackOverflowException> がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="4c341-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
-   <span data-ttu-id="4c341-113">特定の条件下では、メソッドに渡された構造体が、リリース ビルドの値の型ではなく、参照型として扱われます。</span><span class="sxs-lookup"><span data-stu-id="4c341-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="4c341-114">この問題の兆候の 1 つは、コレクション内の個々の項目が予期しない順序で表示されることです。</span><span class="sxs-lookup"><span data-stu-id="4c341-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
-   <span data-ttu-id="4c341-115">特定の条件下では、最適化が有効な場合、高ビットが設定された <xref:System.UInt16> 値が正しく比較されません。</span><span class="sxs-lookup"><span data-stu-id="4c341-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
-   <span data-ttu-id="4c341-116">特定の条件下では、特に、配列値の初期化中に、<xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL 命令でのメモリ初期化により、正しくない値でメモリが初期化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="4c341-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="4c341-117">その結果、ハンドルされない例外または正しくない出力が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="4c341-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
-   <span data-ttu-id="4c341-118">特定のまれな条件下では、コンパイラの最適化が有効な場合に、条件付きのビット テストで正しくない <xref:System.Boolean> 値が返されたり、例外がスローされたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="4c341-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
-   <span data-ttu-id="4c341-119">特定の条件下では、`if` ステートメントを使用して、`try` ブロックの開始前と `try` ブロックの終了時の条件をテストし、同じ条件を `catch` または `finally` ブロックで評価する場合、新しい 64 ビット JIT コンパイラが、コードの最適化の際に `catch` または `finally` ブロックから `if` 条件を削除します。</span><span class="sxs-lookup"><span data-stu-id="4c341-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="4c341-120">その結果、`catch` または `finally` ブロックの `if` ステートメント内のコードは無条件で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4c341-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="4c341-121">既知の問題の軽減策</span><span class="sxs-lookup"><span data-stu-id="4c341-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="4c341-122">上記の問題が発生する場合は、次のいずれかの方法で解決できます。</span><span class="sxs-lookup"><span data-stu-id="4c341-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
-   <span data-ttu-id="4c341-123">.NET Framework 4.6.2 にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="4c341-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="4c341-124">.NET Framework 4.6.2 に含まれている新しい 64 ビット コンパイラは、これらの既知の問題のそれぞれに対処します。</span><span class="sxs-lookup"><span data-stu-id="4c341-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
-   <span data-ttu-id="4c341-125">Windows Update を実行して、Windows のバージョンが最新のものであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4c341-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="4c341-126">.NET Framework 4.6 および 4.6.1 へのサービス更新により、ボックス化解除操作での <xref:System.NullReferenceException> を除き、これらの問題のそれぞれに対処することができます。</span><span class="sxs-lookup"><span data-stu-id="4c341-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
-   <span data-ttu-id="4c341-127">古い 64 ビット JIT コンパイラでコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="4c341-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="4c341-128">この方法の詳細については、「[その他の問題の軽減策](#Other)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c341-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="4c341-129">その他の問題の軽減策</span><span class="sxs-lookup"><span data-stu-id="4c341-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="4c341-130">古い 64 ビット コンパイラと新しい 64 ビット JIT コンパイラでコンパイルされたコードの動作、またはアプリのデバッグ バージョンとリリース バージョン (両方とも新しい 64 ビット JIT コンパイラでコンパイル) の動作に違いが見られる場合は、次のようにして、古い 64 ビット JIT コンパイラでアプリをコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="4c341-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
-   <span data-ttu-id="4c341-131">アプリケーションごとに、アプリケーションの構成ファイルに [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) 要素を追加できます。</span><span class="sxs-lookup"><span data-stu-id="4c341-131">On a per-application basis, you can add the [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="4c341-132">次のように新しい 64 ビット JIT コンパイラでのコンパイルを無効にし、代わりに従来の 64 ビット JIT コンパイラを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c341-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="4c341-133">ユーザーごとに、`useLegacyJit` という `REG_DWORD` 値をレジストリの `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` キーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="4c341-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="4c341-134">値を 1 にすると、従来の 64 ビット JIT コンパイラが有効になり、値を 0 にすると、従来の 64 ビット JIT コンパイラが無効になり、新しい 64 ビット JIT コンパイラが有効になります。</span><span class="sxs-lookup"><span data-stu-id="4c341-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
-   <span data-ttu-id="4c341-135">コンピューターごとに、`useLegacyJit` という名前の `REG_DWORD` 値をレジストリの `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` キーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="4c341-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="4c341-136">値を 1 にすると、従来の 64 ビット JIT コンパイラが有効になり、値を 0 にすると、従来の 64 ビット JIT コンパイラが無効になり、新しい 64 ビット JIT コンパイラが有効になります。</span><span class="sxs-lookup"><span data-stu-id="4c341-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="4c341-137">[Microsoft Connect](https://connect.microsoft.com/VisualStudio) でバグを報告し、問題を弊社に知らせることもできます。</span><span class="sxs-lookup"><span data-stu-id="4c341-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c341-138">参照</span><span class="sxs-lookup"><span data-stu-id="4c341-138">See Also</span></span>  
 [<span data-ttu-id="4c341-139">ランタイムの変更点</span><span class="sxs-lookup"><span data-stu-id="4c341-139">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 [<span data-ttu-id="4c341-140">\<useLegacyJit> 要素</span><span class="sxs-lookup"><span data-stu-id="4c341-140">\<useLegacyJit> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
