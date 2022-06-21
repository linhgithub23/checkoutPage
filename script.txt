$( document ).ready ( function ()
{
    console.log ( 'ready!' );
    $('[data-toggle="tooltip"]').tooltip();
    var template = $( '#template' ).html ();
    Mustache.parse ( template );
    var rendered = Mustache.render ( template, get_basket () );
    $( '#template' ).html ( rendered );
    if ( $('.basket-body').hasScrollBar () )
    {
        $('.column-titles').addClass('fix-overflow');
        $('.basket-body').niceScroll({autohidemode: true,cursorcolor:"#ffffff",cursorborder:"1px solid #D0D0D0",cursorborderradius: "0",background: "#ffffff"});
    }
    else
    {
        $('.column-titles').removeClass('fix-overflow');
    }
    
    $('.card-expiration').datepicker({
    format: "mm/yyyy",
    startView: "months", 
    minViewMode: "months"        
});
});

function get_basket ()
{
    var products =
    [ 
        { name: "Tui xach Tote", additional: "Additional Informations", quantity: 1, unit: "pc", price: 1699000, thumbnail: "http://via.placeholder.com/200x200" }
        
        
    ]
    return { "products": products, "order_number": "1-23-456789A", "subtotal": 1699000, "taxes": 0, "shipping_cost": 810, "total": 1699000, "currency": "₫" };
}

//https://stackoverflow.com/questions/4814398/how-can-i-check-if-a-scrollbar-is-visible
(function($) {
    $.fn.hasScrollBar = function() {
        return this.get(0).scrollHeight > this.height();
    }
})(jQuery);