---
title: "必須の引数とオーバーロード グループ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fae9759faa6ae5e2fa65417c6ef5767330f6d9c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="74fd6-102">必須の引数とオーバーロード グループ</span><span class="sxs-lookup"><span data-stu-id="74fd6-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="74fd6-103">アクティビティは、アクティビティの実行を有効にするためには特定の引数をバインドする必要があるように構成できます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="74fd6-104">`RequiredArgument` 属性は、アクティビティの特定の引数が必須であることを示す場合に使用します。また、`OverloadGroup` 属性は、必須の引数のカテゴリをグループ化する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="74fd6-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="74fd6-105">これらの属性を使用することで、アクティビティ作成者は、単純なアクティビティ検証の構成も複雑な構成も適用できます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="74fd6-106">必須の引数の使用</span><span class="sxs-lookup"><span data-stu-id="74fd6-106">Using Required Arguments</span></span>  
 <span data-ttu-id="74fd6-107">アクティビティで `RequiredArgument` 属性を使用するためには、<xref:System.Activities.RequiredArgumentAttribute> を使用して目的の引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="74fd6-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="74fd6-108">次の例では、2 つの必須引数がある `Add` アクティビティが定義されています。</span><span class="sxs-lookup"><span data-stu-id="74fd6-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="74fd6-109">また、XAML では、必須引数の指定に <xref:System.Activities.RequiredArgumentAttribute> も使用されます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="74fd6-110">この例では、3 つの引数を使用して `Add` アクティビティを定義し、<xref:System.Activities.Statements.Assign%601> アクティビティを使用して追加操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="74fd6-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 <span data-ttu-id="74fd6-111">アクティビティが使用され、いずれかの必須引数がバインドされていない場合は、次の検証エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="74fd6-112">**必須のアクティビティ引数 'Operand1' の値が指定されませんでした。**</span><span class="sxs-lookup"><span data-stu-id="74fd6-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="74fd6-113">確認し、検証エラーおよび警告の処理では、次を参照してください。[アクティビティの検証を呼び出す](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)です。</span><span class="sxs-lookup"><span data-stu-id="74fd6-113"> about checking for and handling validation errors and warnings, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="74fd6-114">オーバーロード グループの使用</span><span class="sxs-lookup"><span data-stu-id="74fd6-114">Using Overload Groups</span></span>  
 <span data-ttu-id="74fd6-115">オーバーロード グループには、あるアクティビティ内で有効である引数の組み合わせを示すメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="74fd6-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="74fd6-116">引数は <xref:System.Activities.OverloadGroupAttribute> を使用してグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="74fd6-117">各グループには、<xref:System.Activities.OverloadGroupAttribute> によって指定される名前が与えられます。アクティビティが有効なのは、オーバーロード グループに含まれる 1 つの引数セットのみがバインドされる場合です。</span><span class="sxs-lookup"><span data-stu-id="74fd6-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>, The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="74fd6-118">取得された次の例で、 [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md)サンプルについては、`CreateLocation`クラスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="74fd6-118">In the following example, taken from the [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) sample, a `CreateLocation` class is defined.</span></span>  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }                  
}  
```  
  
 <span data-ttu-id="74fd6-119">このアクティビティの目的は、米国内の場所を指定することです。</span><span class="sxs-lookup"><span data-stu-id="74fd6-119">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="74fd6-120">これを行うために、アクティビティのユーザーは、3 つある引数グループの 1 つを使用して場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-120">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="74fd6-121">有効な組み合わせで引数を指定するために、3 種類のオーバーロード グループを定義しています。</span><span class="sxs-lookup"><span data-stu-id="74fd6-121">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="74fd6-122">`G1` には `Latitude` および `Longitude` の引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-122">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="74fd6-123">`G2` には `Street`、`City`、および `State` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-123">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="74fd6-124">`G3` には `Street` および `Zip` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-124">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="74fd6-125">`Name` も必要な引数ですが、オーバーロード グループの一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="74fd6-125">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="74fd6-126">このアクティビティが有効であるためには、`Name` が、1 つのオーバーロード グループのみに含まれるすべての引数とバインドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="74fd6-126">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="74fd6-127">次の例から取得、[データベース アクセス アクティビティ](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md)サンプルを 2 つのオーバー ロード グループがある:`ConnectionString`と`ConfigFileSectionName`です。</span><span class="sxs-lookup"><span data-stu-id="74fd6-127">In the following example, taken from the [Database Access Activities](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="74fd6-128">このアクティビティが有効であるためには、引数 `ProviderName` および `ConnectionString` がバインドされているか、または引数 `ConfigName` がバインドされている必要があります。両方がバインドされている場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="74fd6-128">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
 <span data-ttu-id="74fd6-129">オーバーロード グループを定義するときは次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="74fd6-129">When defining an overload group:</span></span>  
  
-   <span data-ttu-id="74fd6-130">オーバーロード グループを別のオーバーロード グループのサブセットまたは等価セットにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="74fd6-130">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="74fd6-131">この規則には例外が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="74fd6-131">There is one exception to this rule.</span></span> <span data-ttu-id="74fd6-132">オーバーロード グループが別のオーバーロード グループのサブセットであり、サブセットに `RequiredArgument` が `false` である引数のみが含まれている場合、オーバーロード グループは有効です。</span><span class="sxs-lookup"><span data-stu-id="74fd6-132">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
-   <span data-ttu-id="74fd6-133">複数のオーバーロード グループが重なり合うように定義することは可能です。ただし、グループの共通部分には、一方または両方のオーバーロード グループの必須引数すべてを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="74fd6-133">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="74fd6-134">前の例では、オーバーロード グループ `G2` および `G3` が重なり合っていますが、共通部分に一方または両方のグループの引数すべてを含めてはいないため、有効です。</span><span class="sxs-lookup"><span data-stu-id="74fd6-134">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="74fd6-135">オーバーロード グループの引数をバインドするときは次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="74fd6-135">When binding arguments in an overload group:</span></span>  
  
-   <span data-ttu-id="74fd6-136">オーバーロード グループ内の `RequiredArgument` 引数すべてがバインドされている場合、そのグループはバインドされていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-136">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
-   <span data-ttu-id="74fd6-137">グループに `RequiredArgument` 引数がなく、1 つ以上の引数がバインドされている場合、そのグループはバインドされていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="74fd6-137">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
-   <span data-ttu-id="74fd6-138">バインドされているオーバーロード グループが 1 つもない状態は、検証エラーになります。ただし、`RequiredArgument` 引数を 1 つも含まないオーバーロード グループが 1 つある場合は有効です。</span><span class="sxs-lookup"><span data-stu-id="74fd6-138">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
-   <span data-ttu-id="74fd6-139">複数のオーバーロード グループをバインドすることはできません。つまり、1 つのオーバーロード グループの必須引数すべてをバインドしているのに加えて、別のオーバーロード グループのいずれかの引数もバインドしている場合は、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="74fd6-139">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
