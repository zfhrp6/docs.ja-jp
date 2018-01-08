---
title: "カスタム属性へのアクセス"
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
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0980488f3093bfcaedc730bac126b1b5b6505187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="1269d-102">カスタム属性へのアクセス</span><span class="sxs-lookup"><span data-stu-id="1269d-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="1269d-103">属性がプログラム要素に関連付けられると、リフレクションを使用して、その存在と値をクエリすることができます。</span><span class="sxs-lookup"><span data-stu-id="1269d-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="1269d-104">.NET Framework バージョン 1.0 および 1.1 では、カスタム属性は実行コンテキストで検証されます。</span><span class="sxs-lookup"><span data-stu-id="1269d-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="1269d-105">.NET Framework バージョン 2.0 では、新しい読み込みコンテキスト (リフレクションのみのコンテキスト) が提供されます。これを使用して、実行のために読み込むことができないコードを検証できます。</span><span class="sxs-lookup"><span data-stu-id="1269d-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="1269d-106">リフレクションのみのコンテキスト</span><span class="sxs-lookup"><span data-stu-id="1269d-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="1269d-107">リフレクションのみのコンテキストに読み込まれたコードは、実行することができません。</span><span class="sxs-lookup"><span data-stu-id="1269d-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="1269d-108">つまり、コンストラクターを実行する必要があるため、カスタム属性のインスタンスは作成できないということです。</span><span class="sxs-lookup"><span data-stu-id="1269d-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="1269d-109">リフレクションのみのコンテキストにカスタム属性を読み込み、検証するには、<xref:System.Reflection.CustomAttributeData> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1269d-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="1269d-110">静的な <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> メソッドの適切なオーバーロードを使用して、このクラスのインスタンスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="1269d-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1269d-111">「[方法: リフレクションのみのコンテキストにアセンブリを読み込む](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1269d-111">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="1269d-112">実行コンテキスト</span><span class="sxs-lookup"><span data-stu-id="1269d-112">The Execution Context</span></span>  
 <span data-ttu-id="1269d-113">実行コンテキストの属性をクエリする主なリフレクション メソッドは、<xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> と <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="1269d-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="1269d-114">カスタム属性のアクセシビリティは、添付されているアセンブリに関してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="1269d-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="1269d-115">これは、カスタム属性が添付されているアセンブリの型のメソッドが、カスタム属性のコンストラクターを呼び出すことができるかどうかをチェックするのと同じです。</span><span class="sxs-lookup"><span data-stu-id="1269d-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="1269d-116"><xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> などのメソッドは、型引数の可視性とアクセシビリティをチェックします。</span><span class="sxs-lookup"><span data-stu-id="1269d-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="1269d-117">ユーザー定義型を含むアセンブリのコードのみが、**GetCustomAttributes** を使用する型のカスタム属性を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="1269d-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="1269d-118">次の C# の例は、一般的なカスタム属性の設計パターンです。</span><span class="sxs-lookup"><span data-stu-id="1269d-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="1269d-119">これは、ランタイムのカスタム属性のリフレクション モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="1269d-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 <span data-ttu-id="1269d-120">このランタイムで **GetLanguage** メソッドに添付されている公開のカスタム属性の型 <xref:System.ComponentModel.DescriptionAttribute> のカスタム属性を取得しようとしている場合、次のアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="1269d-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1.  <span data-ttu-id="1269d-121">ランタイムは、**Type.GetCustomAttributes**(Type *type*) の型引数 **DescriptionAttribute** が公開であることをチェックするため、表示およびアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="1269d-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2.  <span data-ttu-id="1269d-122">ランタイムは、**DescriptionAttribute** から派生するユーザー定義型 **MyDescriptionAttribute** が **System.Web.DLL** アセンブリ内で表示およびアクセスできることをチェックします。これは、メソッド **GetLanguage**() に添付されている場所です。</span><span class="sxs-lookup"><span data-stu-id="1269d-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3.  <span data-ttu-id="1269d-123">ランタイムは、**MyDescriptionAttribute** のコンストラクターが、**System.Web.DLL** アセンブリ内で表示およびアクセスできることをチェックします。</span><span class="sxs-lookup"><span data-stu-id="1269d-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4.  <span data-ttu-id="1269d-124">ランタイムは、カスタム属性のパラメーターを使って **MyDescriptionAttribute** のコンストラクターを呼び出し、呼び出し元に新しいオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1269d-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="1269d-125">カスタム属性のリフレクション モデルは、型が定義されているアセンブリの外にあるユーザー定義型のインスタンスをリークする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1269d-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="1269d-126">これは、**RuntimeMethodInfo** オブジェクトの配列を返す <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> など、ユーザー定義型のインスタンスを返すランタイム システム ライブラリのメンバーと同様です。</span><span class="sxs-lookup"><span data-stu-id="1269d-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="1269d-127">クライアントがユーザー定義のカスタム属性の型に関する情報を検出できないようにするには、型のメンバーを非公開に定義します。</span><span class="sxs-lookup"><span data-stu-id="1269d-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="1269d-128">次の例では、カスタム属性にアクセスできるリフレクションを使用する基本的な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1269d-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1269d-129">参照</span><span class="sxs-lookup"><span data-stu-id="1269d-129">See Also</span></span>  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1269d-130">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="1269d-130">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [<span data-ttu-id="1269d-131">リフレクションに関するセキュリティ上の考慮事項</span><span class="sxs-lookup"><span data-stu-id="1269d-131">Security Considerations for Reflection</span></span>](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
