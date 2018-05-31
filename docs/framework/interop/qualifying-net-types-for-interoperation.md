---
title: 相互運用のための .NET 型の要件
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: baa5b9f250fe7117838f936b09b050ba500b7209
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389045"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="cb3ad-102">相互運用のための .NET 型の要件</span><span class="sxs-lookup"><span data-stu-id="cb3ad-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="cb3ad-103">COM アプリケーションにアセンブリ内の型を公開する場合は、設計時に COM 相互運用の要件を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="cb3ad-104">以下のガイドラインに従うと、マネージ型 (クラス、インターフェイス、構造体、列挙型) は COM の型とシームレスに統合します。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="cb3ad-105">クラスは、インターフェイスを明示的に実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="cb3ad-106">COM 相互運用は、クラスのすべてのメンバーとその基底クラスのメンバーを含むインターフェイスを自動的に生成するメカニズムを備えていますが、明示的なインターフェイスを提供する方がはるかによい方法です。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="cb3ad-107">自動的に生成されるインターフェイスは、クラス インターフェイスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="cb3ad-108">ガイドラインについては、「[クラス インターフェイスの概要](com-callable-wrapper.md#introducing-the-class-interface)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="cb3ad-109">インターフェイス定義言語 (IDL) またはそれと同等のものを使う代わりに、Visual Basic、C#、C++ を使ってコードにインターフェイス定義を組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="cb3ad-110">構文の詳細については、言語のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="cb3ad-111">マネージ型はパブリックにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="cb3ad-112">アセンブリ内のパブリック型のみが登録されて、タイプ ライブラリにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="cb3ad-113">その結果、パブリック型のみが COM に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="cb3ad-114">マネージ型は、COM に公開されない可能性がある他のマネージ コードに機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="cb3ad-115">たとえば、パラメーター化されたコンストラクター、静的メソッド、および定数フィールドは、COM クライアントに公開されません。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="cb3ad-116">さらに、ランタイムが、ある型に、またはある型からデータをマーシャリングすると、データがコピーまたは変換される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="cb3ad-117">メソッド、プロパティ、フィールド、イベントは、パブリックである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="cb3ad-118">また、パブリック型のメンバーを COM に表示させる場合は、メンバーもパブリックにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="cb3ad-119">アセンブリ、パブリック型、またはパブリック型のパブリック メンバーの可視性は、<xref:System.Runtime.InteropServices.ComVisibleAttribute> を適用することにより制限できます。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="cb3ad-120">既定では、すべてのパブリック型とメンバーが可視になります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="cb3ad-121">型では、既定のパブリック コンストラクターを COM からアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="cb3ad-122">マネージ パブリック型のみが COM に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="cb3ad-123">ただし、既定のパブリック コンストラクター (引数のないコンストラクター) がないと、COM クライアントは型を作成できません。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="cb3ad-124">その場合でも、型が他の方法でアクティブ化されると、COM クライアントは型を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="cb3ad-125">型を抽象にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="cb3ad-126">COM クライアントも .NET クライアントも、抽象型は作成できません。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="cb3ad-127">COM にエクスポートされるとき、マネージ型の継承階層はフラット化されます。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="cb3ad-128">マネージ環境とアンマネージ環境では、バージョン管理も異なります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="cb3ad-129">COM に公開された型は、他のマネージ型とバージョン管理特性が異なります。</span><span class="sxs-lookup"><span data-stu-id="cb3ad-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3ad-130">参照</span><span class="sxs-lookup"><span data-stu-id="cb3ad-130">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>  
 [<span data-ttu-id="cb3ad-131">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="cb3ad-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="cb3ad-132">クラス インターフェイスの概要</span><span class="sxs-lookup"><span data-stu-id="cb3ad-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)  
 [<span data-ttu-id="cb3ad-133">相互運用固有の属性の適用</span><span class="sxs-lookup"><span data-stu-id="cb3ad-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)  
 [<span data-ttu-id="cb3ad-134">COM 用のアセンブリのパッケージ化</span><span class="sxs-lookup"><span data-stu-id="cb3ad-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
