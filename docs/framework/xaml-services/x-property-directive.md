---
title: x:Property ディレクティブ
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 0d554d8ba4d69b4c2d4cc01f3965ade7e508bb0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="xproperty-directive"></a><span data-ttu-id="8c11d-102">x:Property ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="8c11d-102">x:Property Directive</span></span>
<span data-ttu-id="8c11d-103">マークアップで XAML プロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="8c11d-103">Declares a XAML property in markup.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="8c11d-104">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="8c11d-104">XAML Object Element Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8c11d-105">XAML 値</span><span class="sxs-lookup"><span data-stu-id="8c11d-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="8c11d-106">XAML 運用環境のバッキング クラスまたは部分クラスの名前。</span><span class="sxs-lookup"><span data-stu-id="8c11d-106">Name of the backing class or partial class for the XAML production.</span></span>|  
|`propertyName`|<span data-ttu-id="8c11d-107">定義されるプロパティのメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="8c11d-107">Member name of the property being defined.</span></span>|  
|`propertyType`|<span data-ttu-id="8c11d-108">このプロパティの型を指定する型名 (またはその他の文字列の形式、フレームワーク固有)。</span><span class="sxs-lookup"><span data-stu-id="8c11d-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c11d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="8c11d-109">Remarks</span></span>  
 <span data-ttu-id="8c11d-110">.NET Framework XAML サービス実装では、</span><span class="sxs-lookup"><span data-stu-id="8c11d-110">In the .NET Framework XAML Services implementation, .</span></span> <span data-ttu-id="8c11d-111">`x:Property` には直接の型のバッキングはありませんが、<xref:System.Windows.Markup.PropertyDefinition> クラスによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8c11d-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="8c11d-112">XAML ノード ストリームでは、`x:Property` 要素は、XAML 言語の XAML 名前空間から `Property` という名前のメンバーとして表されます。</span><span class="sxs-lookup"><span data-stu-id="8c11d-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="8c11d-113">メンバー `Property` は、マークアップによって宣言された属性を保持します。</span><span class="sxs-lookup"><span data-stu-id="8c11d-113">The member `Property` hold attributes as declared by markup.</span></span>  
  
 <span data-ttu-id="8c11d-114">`Name` と `Type` の意味は .NET Framework XAML サービス レベルでは割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="8c11d-114">The meaning of `Name` and `Type` are not assigned at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="8c11d-115">これらは、特定のフレームワークによって課される可能性がある規則の下で後に解釈される文字列の値として、初期の XAML ノード ストリームに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8c11d-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="8c11d-116">意味は、実装によって、XAML の名前および XAML 型の意味と揃えるか、バッキング型のシステムでのみ有効になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8c11d-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>  
  
 <span data-ttu-id="8c11d-117">マークアップでメンバーの定義を指定する手段として `x:Members` の実用的な使用法をサポートするため、メンバーを変更可能なクラスに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c11d-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="8c11d-118">目的とするモデルは、`x:Members` が `x:Class` を指定する型のメンバーとして存在することです。</span><span class="sxs-lookup"><span data-stu-id="8c11d-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="8c11d-119">ただし、型とメンバーを関連付けたり、動的メンバーの定義を作成したりするメカニズムは、.NET Framework XAML サービス レベルではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8c11d-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="8c11d-120">これは、XAML のメンバーの定義をサポートするアプリケーション モデルがある個々のフレームワークに残されています。</span><span class="sxs-lookup"><span data-stu-id="8c11d-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="8c11d-121">一般に、XAML をマークアップ コンパイルするとともに、XAML と分離コードの統合または純粋な XAML からのアセンブリの生成を行う MSBUILD のビルド操作が、この機能をサポートするために必要です。</span><span class="sxs-lookup"><span data-stu-id="8c11d-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="8c11d-122">Windows Workflow Foundation の x:Property</span><span class="sxs-lookup"><span data-stu-id="8c11d-122">x:Property for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="8c11d-123">Windows Workflow Foundation では、 `x:Property` は、全体が XAML で構成されるカスタム アクティビティのメンバーや、分離コードを含むアクティビティ デザイナーの XAML で定義された動的メンバーを定義します。</span><span class="sxs-lookup"><span data-stu-id="8c11d-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="8c11d-124">`x:Class` は、XAML の運用環境のルート要素にも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c11d-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="8c11d-125">これは、.NET Framework XAML サービス レベルの要件ではありませんが、全般にカスタム アクティビティと Windows Workflow Foundation の XAML をサポートする MSBUILD のビルド アクションによって XAML の運用環境が読み込まれるときの要件になります。</span><span class="sxs-lookup"><span data-stu-id="8c11d-125">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="8c11d-126">Windows Workflow Foundation が目的の値として、純粋な XAML 型名を使用しない、 `x:Property` `Type`属性があり、ここで文書化されていない規約を代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="8c11d-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="8c11d-127">詳細については、次を参照してください。[動的アクティビティの作成](http://msdn.microsoft.com/library/dd807392.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="8c11d-127">For more information, see [Dynamic Activity Creation](http://msdn.microsoft.com/library/dd807392.aspx).</span></span>
