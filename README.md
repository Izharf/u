<?php
/**
 * The template for displaying archive pages
 */

get_header();

if ( have_posts() ) : ?>
    <div class="blog-archive-container">
        <header class="archive-header">
            <h1><?php the_archive_title(); ?></h1>
            <p><?php the_archive_description(); ?></p>
        </header>

        <div class="archive-content">
            <div class="posts-grid">
                <?php
                // Start the Loop.
                while ( have_posts() ) :
                    the_post(); ?>
                    
                   
                        
                        <div class="post-details">
                            <div class="post-thumbnail">
                                <a href="<?php the_permalink(); ?>">
                                    <?php the_post_thumbnail('medium'); ?>
                                </a>
 <div class="post-date">
                            <span class="day"><?php echo get_the_date('d'); ?></span>
                         
                            <span class="month"><?php echo get_the_date('M y'); ?></span>
                          
                        
                        </div>
                            </div>
                                 <div class="archive-post">
                       


                            <div class="post-content">
                                <h2 class="post-title">
                                    <a href="<?php the_permalink(); ?>"><?php the_title(); ?></a>
                                </h2>
                                <span class="post-category"><?php the_category(', '); ?></span>
                                <p class="post-excerpt"><?php echo wp_trim_words(get_the_excerpt(), 20, '...'); ?></p>
                                <p class="post-meta">0 comments</p>
                            </div>
                        </div>
                    </div>

                <?php endwhile; ?>
            </div>

            <aside class="sidebar">
                <div class="search-box">
                    <form method="get" action="<?php echo home_url(); ?>">
                        <input type="search" name="s" placeholder="Search...">
                        <button type="submit">Search</button>
                    </form>
                </div>

                <div class="categories-box">
                    <h3>Categories</h3>
                    <ul>
                        <?php wp_list_categories(array(
                            'title_li' => '',
                        )); ?>
                    </ul>
                </div>
            </aside>
        </div>

        <div class="pagination">
            <?php the_posts_pagination(); ?>
        </div>

    </div>

<?php else : ?>
    <p><?php _e('Sorry, no posts were found.'); ?></p>
<?php endif;

get_footer();















// single.php file

<?php get_header(); ?>

<div id="primary" class="content-area">
    <main id="main" class="site-main">
        <?php 
        // Ensure this only applies to single posts
        if ( is_single() ) :
            while ( have_posts() ) : the_post(); ?>
                
                <article id="post-<?php the_ID(); ?>" <?php post_class(); ?>>
                    
                    <div class="post-thumbnail">
                        <?php if ( has_post_thumbnail() ) : ?>
                            <?php the_post_thumbnail( 'large' ); ?>
                        <?php endif; ?>
                    </div>
                    
                    <h1 class="post-title"><?php the_title(); ?></h1>
                    
                    <div class="post-meta">
                        <span class="post-author">By <?php the_author_posts_link(); ?></span>
                        <span class="post-date">Published on <?php echo get_the_date(); ?></span>
                    </div>
                    
                    <div class="post-content">
                        <?php the_content(); ?>
                    </div>

                    <div class="post-taxonomies">
                        <div class="post-categories">
                            <?php esc_html_e( 'Categories: ', 'your-textdomain' ); the_category( ', ' ); ?>
                        </div>
                        <div class="post-tags">
                            <?php the_tags( 'Tags: ', ', ', '' ); ?>
                        </div>
                    </div>
                    
                    <div class="post-navigation">
                        <div class="prev-post">
                            <?php previous_post_link( '%link', '<< Previous Post' ); ?>
                        </div>
                        <div class="next-post">
                            <?php next_post_link( '%link', 'Next Post >>' ); ?>
                        </div>
                    </div>
                    
                    <?php if ( comments_open() || get_comments_number() ) : ?>
                        <div class="post-comments">
                            <?php comments_template(); ?>
                        </div>
                    <?php endif; ?>
                    
                </article>
                
            <?php endwhile;
        endif; ?>
    </main>
</div>

<?php get_footer(); ?>




