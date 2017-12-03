---
title: "カスタム型を使用した Switch アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2fbf80f0038ad830ab35fdb55272e45d8a6bffdc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="aa6b3-102">カスタム型を使用した Switch アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="aa6b3-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="aa6b3-103">このサンプルでは、<xref:System.Activities.Statements.Switch%601> アクティビティを有効にしてユーザー定義の複合型を実行時に評価する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-103">This sample describes how to enable a <xref:System.Activities.Statements.Switch%601> activity to evaluate a user-defined complex type at runtime.</span></span> <span data-ttu-id="aa6b3-104">従来のほとんどの手続き型プログラミング言語で、[切り替える](http://go.microsoft.com/fwlink/?LinkId=180521)ステートメントが変数の条件の評価に基づいて実行ロジックを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-104">In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable.</span></span> <span data-ttu-id="aa6b3-105">従来、`switch` ステートメントは、静的に評価できる式を対象としています。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-105">Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="aa6b3-106">つまり、たとえば C# では、プリミティブ型 (<xref:System.Boolean>、<xref:System.Int32>、<xref:System.String>、列挙型など) のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-106">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="aa6b3-107">カスタム クラスで切り替えを有効にするには、カスタム複合型の値を実行時に評価するロジックを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-107">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="aa6b3-108">このサンプルでは、`Person` という名前のカスタム複合型で切り替えを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-108">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="aa6b3-109">カスタム クラス `Person` では、<xref:System.ComponentModel.TypeConverter> 属性がカスタム <xref:System.ComponentModel.TypeConverter> の名前で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-109">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="aa6b3-110">カスタム クラス `Person` では、<xref:System.Object.Equals%2A> クラスと <xref:System.Object.GetHashCode%2A> クラスがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-110">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   <span data-ttu-id="aa6b3-111">カスタム クラスのインスタンスから文字列への変換、および文字列からカスタム クラスのインスタンスへの変換を行う、カスタム <xref:System.ComponentModel.TypeConverter> クラスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-111">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 <span data-ttu-id="aa6b3-112">このサンプルには、次のファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-112">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="aa6b3-113">**Person.cs**: 定義、`Person`クラスです。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-113">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="aa6b3-114">**PersonConverter.cs**: の型コンバーター、`Person`クラスです。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-114">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="aa6b3-115">**Sequence.xaml**: ワークフローを切り替えられる、`Person`型です。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-115">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="aa6b3-116">**Program.cs**: ワークフローを実行する主な機能です。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-116">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="aa6b3-117">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="aa6b3-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="aa6b3-118">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] に Switch.sln を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-118">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="aa6b3-119">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="aa6b3-120">Ctrl キーを押しながら F5 キーを押してサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-120">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aa6b3-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aa6b3-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aa6b3-123">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa6b3-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="aa6b3-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="aa6b3-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa6b3-125">See Also</span></span>  
 [<span data-ttu-id="aa6b3-126">ビルトイン アクティビティ ライブラリ</span><span class="sxs-lookup"><span data-stu-id="aa6b3-126">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
