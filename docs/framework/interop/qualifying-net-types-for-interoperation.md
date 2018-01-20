---
title: "相互運用のための .NET 型の要件"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a05330a6834b4775e62b7b55aee03526b2a9bbda
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="846ab-102">相互運用のための .NET 型の要件</span><span class="sxs-lookup"><span data-stu-id="846ab-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="846ab-103">COM アプリケーションにアセンブリ内の型を公開する場合は、設計時に COM 相互運用の要件を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="846ab-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="846ab-104">以下のガイドラインに従うと、マネージ型 (クラス、インターフェイス、構造体、列挙型) は COM の型とシームレスに統合します。</span><span class="sxs-lookup"><span data-stu-id="846ab-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="846ab-105">クラスは、インターフェイスを明示的に実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="846ab-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="846ab-106">COM 相互運用は、クラスのすべてのメンバーとその基底クラスのメンバーを含むインターフェイスを自動的に生成するメカニズムを備えていますが、明示的なインターフェイスを提供する方がはるかによい方法です。</span><span class="sxs-lookup"><span data-stu-id="846ab-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="846ab-107">自動的に生成されるインターフェイスは、クラス インターフェイスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="846ab-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="846ab-108">ガイドラインについては、次を参照してください。[クラス インターフェイスの概要](com-callable-wrapper.md#introducing-the-class-interface)です。</span><span class="sxs-lookup"><span data-stu-id="846ab-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="846ab-109">Visual Basic、c#、および C++ を使用して、インターフェイス定義言語 (IDL) またはそれと等価なを使用する代わりに、コード内のインターフェイスの定義を組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="846ab-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="846ab-110">構文の詳細については、言語のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="846ab-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="846ab-111">マネージ型はパブリックにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="846ab-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="846ab-112">アセンブリ内のパブリック型のみが登録されて、タイプ ライブラリにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="846ab-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="846ab-113">その結果、パブリック型のみが COM に表示されます。</span><span class="sxs-lookup"><span data-stu-id="846ab-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="846ab-114">マネージ型は、COM に公開されない可能性がある他のマネージ コードに機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="846ab-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="846ab-115">たとえば、パラメーター化されたコンストラクター、静的メソッド、および定数フィールドは、COM クライアントに公開されません。</span><span class="sxs-lookup"><span data-stu-id="846ab-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="846ab-116">さらに、ランタイムが、ある型に、またはある型からデータをマーシャリングすると、データがコピーまたは変換される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="846ab-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="846ab-117">メソッド、プロパティ、フィールド、イベントは、パブリックである必要があります。</span><span class="sxs-lookup"><span data-stu-id="846ab-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="846ab-118">また、パブリック型のメンバーを COM に表示させる場合は、メンバーもパブリックにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="846ab-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="846ab-119">アセンブリ、パブリック型、またはパブリック型のパブリック メンバーの可視性は、<xref:System.Runtime.InteropServices.ComVisibleAttribute> を適用することにより制限できます。</span><span class="sxs-lookup"><span data-stu-id="846ab-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="846ab-120">既定では、すべてのパブリック型とメンバーが可視になります。</span><span class="sxs-lookup"><span data-stu-id="846ab-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="846ab-121">型では、既定のパブリック コンストラクターを COM からアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="846ab-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="846ab-122">マネージ パブリック型のみが COM に表示されます。</span><span class="sxs-lookup"><span data-stu-id="846ab-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="846ab-123">ただし、既定のパブリック コンストラクター (引数のないコンストラクター) がないと、COM クライアントは型を作成できません。</span><span class="sxs-lookup"><span data-stu-id="846ab-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="846ab-124">その場合でも、型が他の方法でアクティブ化されると、COM クライアントは型を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="846ab-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="846ab-125">型を抽象にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="846ab-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="846ab-126">COM クライアントも .NET クライアントも、抽象型は作成できません。</span><span class="sxs-lookup"><span data-stu-id="846ab-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="846ab-127">COM にエクスポートされるとき、マネージ型の継承階層はフラット化されます。</span><span class="sxs-lookup"><span data-stu-id="846ab-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="846ab-128">マネージ環境とアンマネージ環境では、バージョン管理も異なります。</span><span class="sxs-lookup"><span data-stu-id="846ab-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="846ab-129">COM に公開された型は、他のマネージ型とバージョン管理特性が異なります。</span><span class="sxs-lookup"><span data-stu-id="846ab-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846ab-130">参照</span><span class="sxs-lookup"><span data-stu-id="846ab-130">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>  
 [<span data-ttu-id="846ab-131">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="846ab-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="846ab-132">クラス インターフェイスの概要</span><span class="sxs-lookup"><span data-stu-id="846ab-132">Introducing the Class Interface</span></span>](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [<span data-ttu-id="846ab-133">相互運用固有の属性の適用</span><span class="sxs-lookup"><span data-stu-id="846ab-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)  
 [<span data-ttu-id="846ab-134">COM 用のアセンブリのパッケージ化</span><span class="sxs-lookup"><span data-stu-id="846ab-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
