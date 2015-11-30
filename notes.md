# Теперь все файлы стилей в одном файле
all.less импортирует остальные файлы less и из всех них получается один all.css. Он и подключается в хедере. 

# Именование
* В БЭМ элементы именуются через два подчеркивания: slider__list, а не slider_list. С одним подчеркиванием — это 
модификатор. Например, slider_small.

# LESS
Вот так писать не надо:

    &_link-more {
        margin-left: 10px;
        display: block;
        width: 120px;
        text-decoration: none;
        color: #fff;
        font-size: 24px;
    }
    &_link-more:hover {
        color: #000;
        text-shadow: 1px 1px 2px #fff, 0 0 1em #fff;
    }

Надо так:

    &_link-more {
        margin-left: 10px;
        display: block;
        width: 120px;
        text-decoration: none;
        color: #fff;
        font-size: 24px;
        &:hover {
            color: #000;
            text-shadow: 1px 1px 2px #fff, 0 0 1em #fff;
        }
    }

# Списки
Не нужно забывать, что у UL и OL по умолчанию есть padding и margin. Зачастую их надо обнулять или ставить свои.

# TODO
Переделать точки в slider-info__list. Значения должны быть выровнены, а точки нужно рисовать в CSS.

# Каждый блок сам по себе
Наприимер, .slider — это один блок. А .slider-header — это уже другой. Если бы это был его элемент (slider__header), 
то стили элемента мы включали бы внутрь блока .slider: 

    .slider {
        &__header { // на выходе будет slider__header
        }
    }

А так мы имеем два блока. Просто один внутри другого. Так меньше вложенности и мы лучше читаем код:

    .slider {
        // ...
    }
    
    .slider-header {
        // ...
    }

# Наведение на родителя
Пример:

    .link {
        .slider-header__item:hover & {
            color: #000;
            text-shadow: 1px 1px 2px #fff, 0 0 1em white;
        }
    }

#Flexbox
В .slider-header я применил флексбоксы.
