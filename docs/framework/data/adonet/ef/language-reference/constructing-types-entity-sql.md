---
title: コンストラクター (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 91ed123132965353ff354282f6850e9ef9cba3d0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="16f7c-102">コンストラクター (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="16f7c-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="16f7c-103"> 次の 3 つの種類のコンス トラクターを提供します。 行コンス トラクター、名前付きの型のコンス トラクター、およびコレクション コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="16f7c-103"> provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="16f7c-104">行コンストラクター</span><span class="sxs-lookup"><span data-stu-id="16f7c-104">Row Constructors</span></span>  
 <span data-ttu-id="16f7c-105">1 つまたは複数の値から構造的に型付けされた匿名レコードを構築するには、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の行コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="16f7c-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="16f7c-106">行コンストラクターの結果の型は、行の構築に使用された値の型に対応するフィールド型を持つ行型です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="16f7c-107">たとえば、次の式が型の値を構築`Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="16f7c-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="16f7c-108">行コンストラクターで式の別名が指定されていなければ、Entity Framework は別名の生成を試みます。</span><span class="sxs-lookup"><span data-stu-id="16f7c-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="16f7c-109">詳細については、「別名規則」セクションを参照してください。[識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-109">For more information, see the "Aliasing Rules" section in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="16f7c-110">次の規則は、行コンストラクターで別名を定義する式に適用されます。</span><span class="sxs-lookup"><span data-stu-id="16f7c-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="16f7c-111">行コンストラクターの式で同じコンストラクターの他の別名を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="16f7c-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="16f7c-112">同じ行コンストラクター内の 2 つの式に同じ別名を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="16f7c-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="16f7c-113">行コンス トラクターの詳細については、次を参照してください。[行](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-113">For more information about row constructors, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="16f7c-114">コレクション コンストラクター</span><span class="sxs-lookup"><span data-stu-id="16f7c-114">Collection Constructors</span></span>  
 <span data-ttu-id="16f7c-115">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のコレクション コンストラクターを使用して、値のリストからマルチセットのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="16f7c-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="16f7c-116">コンストラクターのすべての値は、相互に互換性のある型 `T` でなければなりません。また、コンストラクターは `Multiset<T>` 型のコレクションを生成します。</span><span class="sxs-lookup"><span data-stu-id="16f7c-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="16f7c-117">たとえば、次の式は整数のコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="16f7c-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="16f7c-118">要素の型が確認できないため、空のマルチセット コンストラクターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="16f7c-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="16f7c-119">次の式は無効です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="16f7c-120">詳細については、次を参照してください。 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-120">For more information, see [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="16f7c-121">名前付きの型コンストラクター (NamedType 初期化子)</span><span class="sxs-lookup"><span data-stu-id="16f7c-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="16f7c-122"> では、型コンストラクター (初期化子) を使用して、名前付きの複合型およびエンティティ型のインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="16f7c-122"> allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="16f7c-123">たとえば、次の式は `Person` 型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="16f7c-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="16f7c-124">次の式は、複合型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="16f7c-125">次の式は、入れ子になった複合型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="16f7c-126">次の式は、入れ子になった複合型を持つエンティティのインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="16f7c-127">次の例は、複合型のプロパティを null に初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="16f7c-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="16f7c-128">コンストラクターに対する引数は、型の属性の宣言と同じ順序であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="16f7c-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="16f7c-129">詳細については、次を参照してください。[という名前の型コンス トラクター](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="16f7c-129">For more information, see [Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f7c-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="16f7c-130">See Also</span></span>  
 [<span data-ttu-id="16f7c-131">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="16f7c-131">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="16f7c-132">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="16f7c-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="16f7c-133">型システム</span><span class="sxs-lookup"><span data-stu-id="16f7c-133">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
