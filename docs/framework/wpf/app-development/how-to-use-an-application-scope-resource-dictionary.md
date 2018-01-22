---
title: "方法 : アプリケーション スコープのリソース ディクショナリを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04dbcfb0fa16ceb4d6778ef611e926894d7840e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="7823d-102">方法 : アプリケーション スコープのリソース ディクショナリを使用する</span><span class="sxs-lookup"><span data-stu-id="7823d-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="7823d-103">この例では、アプリケーション スコープのカスタム リソース ディクショナリを定義して、使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7823d-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7823d-104">例</span><span class="sxs-lookup"><span data-stu-id="7823d-104">Example</span></span>  
 <span data-ttu-id="7823d-105"><xref:System.Windows.Application>共有リソースのアプリケーション スコープのストアを公開:<xref:System.Windows.Application.Resources%2A>です。</span><span class="sxs-lookup"><span data-stu-id="7823d-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="7823d-106">既定では、<xref:System.Windows.Application.Resources%2A>プロパティは、のインスタンスを初期化、<xref:System.Windows.ResourceDictionary>型です。</span><span class="sxs-lookup"><span data-stu-id="7823d-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="7823d-107">Get を使用してアプリケーション スコープのプロパティを設定すると、このインスタンスを使用する<xref:System.Windows.Application.Resources%2A>です。</span><span class="sxs-lookup"><span data-stu-id="7823d-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="7823d-108">詳細については、次を参照してください。[する方法: を取得し、アプリケーション スコープ リソース設定](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095)です。</span><span class="sxs-lookup"><span data-stu-id="7823d-108">For more information, see [How to: Get and Set an Application-Scope Resource](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span></span>
  
 <span data-ttu-id="7823d-109">複数のリソースを使用して設定する必要がある場合<xref:System.Windows.Application.Resources%2A>、それらのリソースを格納および設定する代わりに、カスタム リソース ディクショナリを使用できます<xref:System.Windows.Application.Resources%2A>して代わりにします。</span><span class="sxs-lookup"><span data-stu-id="7823d-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="7823d-110">XAML を使用して、カスタム リソース ディクショナリを宣言する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7823d-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="7823d-111">使用して全体のリソース ディクショナリのスワップ<xref:System.Windows.Application.Resources%2A>各テーマが 1 つのリソース ディクショナリでカプセル化された場所を使用すると、アプリケーション スコープのテーマをサポートします。</span><span class="sxs-lookup"><span data-stu-id="7823d-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="7823d-112"><xref:System.Windows.ResourceDictionary> を設定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="7823d-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="7823d-113">によって公開されるリソース ディクショナリからアプリケーション スコープのリソースを取得する方法を次に示します<xref:System.Windows.Application.Resources%2A>XAML でします。</span><span class="sxs-lookup"><span data-stu-id="7823d-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="7823d-114">コードでリソースも取得する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7823d-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="7823d-115">2 つの考慮事項を使用する場合がある<xref:System.Windows.Application.Resources%2A>です。</span><span class="sxs-lookup"><span data-stu-id="7823d-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="7823d-116">まず、ディクショナリ*キー*オブジェクトは両方の設定とプロパティ値を取得するときに正確に同じオブジェクト インスタンスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7823d-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="7823d-117">(キーに文字列を使用する場合、大文字と小文字が区別されることに注意してください)。2 番目、ディクショナリ*値*がオブジェクト、プロパティ値を取得するときに、値を目的の型に変換しなければならないためです。</span><span class="sxs-lookup"><span data-stu-id="7823d-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7823d-118">参照</span><span class="sxs-lookup"><span data-stu-id="7823d-118">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [<span data-ttu-id="7823d-119">XAML リソース</span><span class="sxs-lookup"><span data-stu-id="7823d-119">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="7823d-120">マージされたリソース ディクショナリ</span><span class="sxs-lookup"><span data-stu-id="7823d-120">Merged Resource Dictionaries</span></span>](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
