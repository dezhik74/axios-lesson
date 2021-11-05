<script lang="jsx">
export default {
    name: "alPosts",
    functional: true,
    props: {
        posts: {
            type: Array,
            default: () => [],
        },
        isError: {
            type: Boolean,
            default: true,
        }
    },
    render(h, {$style, props}) {
        return (
            <div>
                <h3 class={$style.header}> 
                    Привет из компонента
                </h3>
                {
                    !props.isError ? 
                    <div class={$style.postsContainer}>
                        {...props.posts.map(el => 
                            <div class={$style.postCard}>
                                <div class={$style.postTitle}>
                                    {el.title}
                                </div>
                                <div class={$style.postBody}>
                                    {el.body}
                                </div>
                            </div>)
                        }
                    </div> :
                    <div>
                        Ошибка загрузки данных
                    </div>
                }
            </div>
        )
    }
};
</script>

<style module>
.header {
    color: green;
}

    .postsContainer {
        max-width: 1000px;
        margin: auto;
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        grid-gap: 10px;
        
    }

.postCard {
    display: flex;
    flex-direction: column;
    padding: 3px;
    border:darkblue solid 2px;
    border-radius: 10px;
}

.postTitle{
    color: blue;
    min-height: 60px;
    border-bottom: springgreen solid 1px;
    text-align: left;
}

.postBody{
    padding: 5px;
    margin-bottom: 10px;
    text-align: justify;
} 


</style>