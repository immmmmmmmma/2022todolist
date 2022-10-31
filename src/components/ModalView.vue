<template>
<div class="modal">
    <h3>
        <slot name="header"></slot>
    </h3>
    <p>
        <slot name="body"></slot>
    </p>
    <div>
        <button>닫으까?</button>
    </div>
</div>
</template>

<script>
export default {

}
</script>

<style>
    .modal{
        width: 300px;
        height: 200px;
        background: #fff;
        position: fixed;
        left: 50%;
        top: 10%;
        margin-left: -150px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column ;
        gap: 20px;
        border-radius: 20px;
        box-shadow: 0 0 10px rgb(0, 0, 0, 0.3);
    }
</style>