---
title: "COM への .NET Framework コンポーネントの公開"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9451504b64ddaa8dc0ea6b3a0754257b2c8b3824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="d5e82-102">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="d5e82-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="d5e82-103">.NET 型の記述とその型をアンマネージ コードから使用することは、開発者にとっては個別のアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="d5e82-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="d5e82-104">このセクションでは、COM クライアントと相互運用するマネージ コードの記述のためのいくつかのヒントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d5e82-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
-   <span data-ttu-id="d5e82-105">[相互運用のための .NET 型の要件を満たす](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e82-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="d5e82-106">COM に対して公開するすべてのマネージ型、マネージ メソッド、マネージ プロパティ、マネージ フィールド、およびマネージ イベントは、パブリックとしてください。</span><span class="sxs-lookup"><span data-stu-id="d5e82-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="d5e82-107">型は、パブリックな既定のコンストラクターを持っている必要があります。このコンストラクターが、COM を通じて呼び出すことができる唯一のコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="d5e82-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
-   <span data-ttu-id="d5e82-108">[相互運用属性を適用する](../../../docs/framework/interop/applying-interop-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e82-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="d5e82-109">マネージ コード内のカスタム属性は、コンポーネントの相互運用性を強化できます。</span><span class="sxs-lookup"><span data-stu-id="d5e82-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
-   <span data-ttu-id="d5e82-110">[COM 用にアセンブリをパッケージ化する](../../../docs/framework/interop/packaging-an-assembly-for-com.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e82-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="d5e82-111">COM 開発者から、アセンブリの参照と展開に必要な手順をまとめるように求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5e82-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="d5e82-112">さらに、このセクションでは、COM クライアントからマネージ型の使用に関連するタスクを明らかにします。</span><span class="sxs-lookup"><span data-stu-id="d5e82-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="d5e82-113">COM からマネージ型を使用するには</span><span class="sxs-lookup"><span data-stu-id="d5e82-113">To consume a managed type from COM</span></span>  
  
1.  <span data-ttu-id="d5e82-114">[COM にアセンブリを登録する](../../../docs/framework/interop/registering-assemblies-with-com.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e82-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="d5e82-115">アセンブリ (およびタイプ ライブラリ) 内の型は、デザイン時に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5e82-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="d5e82-116">インストーラーでアセンブリが登録されない場合は、Regasm.exe を使用するように COM 開発者に指示します。</span><span class="sxs-lookup"><span data-stu-id="d5e82-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2.  <span data-ttu-id="d5e82-117">[COM から .NET 型を参照する](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e82-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="d5e82-118">COM 開発者は、現在使用しているのと同じツールと手法を使用して、アセンブリ内の型を参照できます。</span><span class="sxs-lookup"><span data-stu-id="d5e82-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3.  <span data-ttu-id="d5e82-119">[.NET オブジェクトを呼び出す](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)。</span><span class="sxs-lookup"><span data-stu-id="d5e82-119">[Call a .NET object](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span></span>  
  
     <span data-ttu-id="d5e82-120">COM 開発者は、アンマネージ型でメソッドを呼び出すのと同じ方法で、.NET オブジェクトでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d5e82-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="d5e82-121">たとえば、COM **CoCreateInstance** API は、.NET オブジェクトをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="d5e82-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4.  <span data-ttu-id="d5e82-122">[COM アクセスに対してアプリケーションを展開する](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)。</span><span class="sxs-lookup"><span data-stu-id="d5e82-122">[Deploy an application for COM access](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).</span></span>  
  
     <span data-ttu-id="d5e82-123">厳格な名前付きのアセンブリは、グローバル アセンブリ キャッシュにインストールすることができ、発行元からの署名が必要です。</span><span class="sxs-lookup"><span data-stu-id="d5e82-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="d5e82-124">厳密な名前のないアセンブリは、クライアントのアプリケーション ディレクトリにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5e82-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e82-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5e82-125">See Also</span></span>  
 [<span data-ttu-id="d5e82-126">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="d5e82-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="d5e82-127">COM 相互運用機能のサンプル: COM クライアントおよび .NET サーバー</span><span class="sxs-lookup"><span data-stu-id="d5e82-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
