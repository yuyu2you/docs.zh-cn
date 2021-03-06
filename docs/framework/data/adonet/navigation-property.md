---
title: 导航属性-ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: afb2043abf70fa92ea7cdf8d1e8246d5cdfdba74
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738383"
---
# <a name="navigation-property"></a>导航属性

*导航属性*是[实体类型](entity-type.md)上的一个可选属性，它允许从[关联](association-type.md)的[一端](association-end.md)导航到另一端。 与其他[属性](property.md)不同，导航属性不包含数据。

导航属性定义包含以下信息：

- 名称。 （必需）

- 导航属性要导航的关联。 （必需）

- 导航属性要导航的关联端。 （必需）

注意，对于关联两端的两种实体类型，导航属性都是可选的。 如果您对于位于关联一端的实体类型定义一个导航属性，则不需要对于位于关联另一端的实体类型定义导航属性。

导航属性的数据类型由其远程[关联端](association-end.md)的重[数](association-end-multiplicity.md)决定。 例如，假设导航属性 `OrdersNavProp` 存在于 `Customer` 实体类型上并导航 `Customer` 与 `Order` 之间的一对多关系。 因为导航属性的远程关联端的重数为 many （\*），所以其数据类型为集合（的 `Order`）。 同样，如果导航属性 `CustomerNavProp` 存在于 `Order` 实体类型上，但由于远程端的重数为“一 (1)”，所以其数据类型应为 `Customer`。

## <a name="example"></a>示例

下图显示了一个具有三个实体类型的概念模型：`Book`、`Publisher` 和 `Author`。 导航属性 `Publisher` 和 `Authors` 都是在 Book 实体类型上定义的。 导航属性 `Books` 是同时在 Publisher 实体类型和 `Author` 实体类型上定义的。

 ![显示具有三个实体类型的概念模型的关系图。](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET 实体框架](./ef/index.md)使用一种称为概念架构定义语言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的域特定语言（DSL）来定义概念模型。 下面的 CSDL 定义了上图中显示的 `Book` 实体类型。

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

请注意，XML 特性用于传达定义导航属性所需的信息：特性 `Name` 包含属性的名称，`Relationship` 包含属性要导航的关联名称，而 `FromRole` 和 `ToRole` 则包含关联各端。

## <a name="see-also"></a>请参阅

- [实体数据模型关键概念](entity-data-model-key-concepts.md)
- [实体数据模型](entity-data-model.md)
- [关系、导航属性和外键](/ef/ef6/fundamentals/relationships)
