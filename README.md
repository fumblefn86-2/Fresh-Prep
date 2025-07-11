import React from 'react';
import { Tabs } from 'expo-router';
import { Home, ShoppingBag, Leaf, CalendarClock, User } from 'lucide-react-native';
import Colors from '@/constants/colors';
import CartIcon from '@/components/CartIcon';

export default function TabLayout() {
  return (
    <Tabs
      screenOptions={{
        tabBarActiveTintColor: Colors.light.primary,
        tabBarInactiveTintColor: Colors.light.textLight,
        tabBarStyle: {
          borderTopWidth: 1,
          borderTopColor: Colors.light.border,
          height: 60,
          paddingBottom: 8,
          paddingTop: 8,
        },
        tabBarLabelStyle: {
          fontSize: 12,
          fontWeight: '500',
        },
        headerStyle: {
          backgroundColor: Colors.light.background,
        },
        headerTitleStyle: {
          fontWeight: '600',
        },
        headerShadowVisible: false,
      }}
    >
      <Tabs.Screen
        name="index"
        options={{
          title: 'Home',
          tabBarIcon: ({ color }) => <Home size={24} color={color} />,
          headerRight: () => <CartIcon />,
        }}
      />
      <Tabs.Screen
        name="shop"
        options={{
          title: 'Shop',
          tabBarIcon: ({ color }) => <ShoppingBag size={24} color={color} />,
          headerRight: () => <CartIcon />,
        }}
      />
      <Tabs.Screen
        name="impact"
        options={{
          title: 'Impact',
          tabBarIcon: ({ color }) => <Leaf size={24} color={color} />,
        }}
      />
      <Tabs.Screen
        name="subscriptions"
        options={{
          title: 'Subscriptions',
          tabBarIcon: ({ color }) => <CalendarClock size={24} color={color} />,
        }}
      />
      <Tabs.Screen
        name="profile"
        options={{
          title: 'Profile',
          tabBarIcon: ({ color }) => <User size={24} color={color} />,
        }}
      />
    </Tabs>
  );
}
import React from 'react';
import { StyleSheet, Text, View, ScrollView, Dimensions } from 'react-native';
import { Stack } from 'expo-router';
import { Leaf, Droplets, Wind, Info } from 'lucide-react-native';
import Colors from '@/constants/colors';
import { useUserStore } from '@/store/user-store';
import ImpactCard from '@/components/ImpactCard';

const { width } = Dimensions.get('window');

export default function ImpactScreen() {
  const user = useUserStore((state) => state.user);
  const impactStats = user?.impactStats || {
    foodWasteSaved: 0,
    carbonFootprintReduced: 0,
    waterSaved: 0,
    ordersPlaced: 0
  };

  return (
    <>
      <Stack.Screen
        options={{
          title: 'Your Impact',
          headerStyle: {
            backgroundColor: Colors.light.background,
          },
          headerShadowVisible: false,
        }}
      />
      <ScrollView style={styles.container} showsVerticalScrollIndicator={false}>
        {/* Hero Banner */}
        <View style={styles.heroBanner}>
          <View style={styles.bannerContent}>
            <Leaf size={32} color="#FFFFFF" />
            <Text style={styles.bannerTitle}>Making a Difference</Text>
            <Text style={styles.bannerText}>
              Every order helps reduce food waste and supports sustainable farming
            </Text>
          </View>
        </View>

        {/* Impact Stats */}
        <View style={styles.statsContainer}>
          <View style={styles.statsRow}>
            <ImpactCard
              title="Food Saved"
              value={impactStats.foodWasteSaved}
              unit="lbs"
              type="food"
              index={0}
            />
            <View style={{ width: 12 }} />
            <ImpactCard
              title="Water Saved"
              value={impactStats.waterSaved}
              unit="gal"
              type="water"
              index={1}
            />
          </View>
          <View style={styles.statsRow}>
            <ImpactCard
              title="CO₂ Reduced"
              value={impactStats.carbonFootprintReduced}
              unit="lbs"
              type="carbon"
              index={2}
            />
            <View style={{ width: 12 }} />
            <ImpactCard
              title="Orders Placed"
              value={impactStats.ordersPlaced}
              unit=""
              type="food"
              index={3}
            />
          </View>
        </View>

        {/* Information Section */}
        <View style={styles.infoSection}>
          <Text style={styles.sectionTitle}>How You Are Helping</Text>
          
          <View style={styles.infoCard}>
            <View style={[styles.infoIconContainer, { backgroundColor: 'rgba(46, 125, 50, 0.1)' }]}>
              <Leaf size={24} color={Colors.light.primary} />
            </View>
            <View style={styles.infoContent}>
              <Text style={styles.infoTitle}>Reducing Food Waste</Text>
              <Text style={styles.infoText}>
                By purchasing pre-cut vegetables and meal kits, you help reduce food waste at farms and processing facilities.
              </Text>
            </View>
          </View>

          <View style={styles.infoCard}>
            <View style={[styles.infoIconContainer, { backgroundColor: 'rgba(33, 150, 243, 0.1)' }]}>
              <Droplets size={24} color="#2196F3" />
            </View>
            <View style={styles.infoContent}>
              <Text style={styles.infoTitle}>Conserving Water</Text>
              <Text style={styles.infoText}>
                Our efficient processing methods use 40% less water compared to traditional food preparation.
              </Text>
            </View>
          </View>

          <View style={styles.infoCard}>
            <View style={[styles.infoIconContainer, { backgroundColor: 'rgba(96, 125, 139, 0.1)' }]}>
              <Wind size={24} color="#607D8B" />
            </View>
            <View style={styles.infoContent}>
              <Text style={styles.infoTitle}>Lower Carbon Footprint</Text>
              <Text style={styles.infoText}>
                Optimized delivery routes and reduced packaging help minimize our environmental impact.
              </Text>
            </View>
          </View>
        </View>

        {/* Goals Section */}
        <View style={styles.goalSection}>
          <Text style={styles.sectionTitle}>Monthly Goals</Text>
          
          <View style={styles.goalCard}>
            <View style={styles.goalProgress}>
              <View style={[styles.goalProgressBar, { width: `${Math.min((impactStats.foodWasteSaved / 50) * 100, 100)}%` }]} />
            </View>
            <Text style={styles.goalText}>
              <Text style={styles.goalHighlight}>{impactStats.foodWasteSaved.toFixed(1)} / 50 lbs</Text> food waste prevented
            </Text>
          </View>

          <View style={styles.goalCard}>
            <View style={styles.goalProgress}>
              <View style={[styles.goalProgressBar, { width: `${Math.min((impactStats.waterSaved / 200) * 100, 100)}%` }]} />
            </View>
            <Text style={styles.goalText}>
              <Text style={styles.goalHighlight}>{impactStats.waterSaved.toFixed(0)} / 200 gallons</Text> water conserved
            </Text>
          </View>

          <View style={styles.goalCard}>
            <View style={styles.goalProgress}>
              <View style={[styles.goalProgressBar, { width: `${Math.min((impactStats.carbonFootprintReduced / 25) * 100, 100)}%` }]} />
            </View>
            <Text style={styles.goalText}>
              <Text style={styles.goalHighlight}>{impactStats.carbonFootprintReduced.toFixed(1)} / 25 lbs</Text> CO₂ emissions reduced
            </Text>
          </View>
        </View>
      </ScrollView>
    </>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: Colors.light.background,
  },
  heroBanner: {
    backgroundColor: Colors.light.primary,
    paddingHorizontal: 20,
    paddingVertical: 32,
    marginBottom: 24,
  },
  bannerContent: {
    alignItems: 'center',
  },
  bannerTitle: {
    fontSize: 24,
    fontWeight: '700',
    color: '#FFFFFF',
    marginBottom: 8,
    marginTop: 16,
  },
  bannerText: {
    fontSize: 14,
    color: '#FFFFFF',
    textAlign: 'center',
    opacity: 0.9,
  },
  statsContainer: {
    paddingHorizontal: 16,
    marginBottom: 24,
  },
  statsRow: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    marginBottom: 16,
  },
  statsSpacer: {
    width: 12,
  },
  infoSection: {
    paddingHorizontal: 16,
    marginBottom: 24,
  },
  sectionTitle: {
    fontSize: 18,
    fontWeight: '600',
    color: Colors.light.text,
    marginBottom: 16,
  },
  infoCard: {
    flexDirection: 'row',
    backgroundColor: Colors.light.card,
    borderRadius: 12,
    padding: 16,
    marginBottom: 12,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.1,
    shadowRadius: 4,
    elevation: 2,
  },
  infoIconContainer: {
    width: 48,
    height: 48,
    borderRadius: 24,
    justifyContent: 'center',
    alignItems: 'center',
    marginRight: 16,
  },
  infoContent: {
    flex: 1,
  },
  infoTitle: {
    fontSize: 16,
    fontWeight: '600',
    color: Colors.light.text,
    marginBottom: 4,
  },
  infoText: {
    fontSize: 14,
    color: Colors.light.textLight,
    lineHeight: 20,
  },
  goalSection: {
    paddingHorizontal: 16,
    marginBottom: 32,
  },
  goalCard: {
    backgroundColor: Colors.light.card,
    borderRadius: 12,
    padding: 16,
    marginBottom: 12,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.1,
    shadowRadius: 4,
    elevation: 2,
  },
  goalProgress: {
    height: 8,
    backgroundColor: 'rgba(76, 175, 80, 0.2)',
    borderRadius: 4,
    marginBottom: 12,
    overflow: 'hidden',
  },
  goalProgressBar: {
    height: '100%',
    backgroundColor: Colors.light.primary,
    borderRadius: 4,
  },
  goalText: {
    fontSize: 14,
    color: Colors.light.textLight,
  },
  goalHighlight: {
    fontWeight: '700',
    color: Colors.light.text,
  },
});
import React, { useState, useEffect } from 'react';
import {
  StyleSheet,
  Text,
  View,
  ScrollView,
  Pressable,
  Dimensions,
  FlatList,
} from 'react-native';
import { Stack, useRouter } from 'expo-router';
import { ShoppingBag, ChevronRight, Leaf, Award } from 'lucide-react-native';
import { Image } from 'expo-image';
import Colors from '@/constants/colors';
import { categories } from '@/mocks/categories';
import { products } from '@/mocks/products';
import { useCartStore } from '@/store/cart-store';
import { useUserStore } from '@/store/user-store';
import AnimatedCategoryCard from '@/components/AnimatedCategoryCard';
import AnimatedProductCard from '@/components/AnimatedProductCard';
import CartIcon from '@/components/CartIcon';

const { width, height } = Dimensions.get('window');
const headerFontSize = width < 375 ? 24 : 28;

export default function HomeScreen() {
  const router = useRouter();
  const user = useUserStore((state) => state.user);
  const featuredProducts = products.filter(p => p.isFeatured).slice(0, 6);
  const popularProducts = products.filter(p => p.isPopular).slice(0, 8);

  const handleSeeAllCategories = () => {
    router.push('/(tabs)/shop');
  };

  const handleSeeAllProducts = () => {
    router.push('/(tabs)/shop');
  };

  const handleImpactPress = () => {
    router.push('/(tabs)/impact');
  };

  const handleCategoryPress = (categoryId: string) => {
    router.push(`/category/${categoryId}`);
  };

  return (
    <>
      <Stack.Screen
        options={{
          title: '',
          headerStyle: {
            backgroundColor: Colors.light.background,
          },
          headerShadowVisible: false,
          headerRight: () => <CartIcon />,
        }}
      />
      <ScrollView
        style={styles.container}
        showsVerticalScrollIndicator={false}
        contentContainerStyle={styles.scrollContent}
      >
        {/* Header */}
        <View style={styles.header}>
          <View style={styles.welcomeContainer}>
            <Text style={styles.welcomeText}>Good morning</Text>
            <Text style={styles.title}>Fresh ingredients, delivered daily</Text>
          </View>
        </View>

        {/* Impact Banner */}
        <Pressable style={styles.impactBanner} onPress={handleImpactPress}>
          <View style={styles.impactContent}>
            <View style={styles.impactIconContainer}>
              <Leaf size={24} color="#FFFFFF" />
            </View>
            <View style={styles.impactTextContainer}>
              <Text style={styles.impactTitle}>Your Impact</Text>
              <Text style={styles.impactSubtitle}>
                {user?.impactStats.foodWasteSaved.toFixed(1) || '0'} lbs food saved this month
              </Text>
            </View>
            <View style={styles.impactBadge}>
              <Award size={16} color={Colors.light.accent} />
            </View>
          </View>
        </Pressable>

        {/* Categories Section */}
        <View style={styles.section}>
          <View style={styles.sectionHeader}>
            <Text style={styles.sectionTitle}>Shop by Category</Text>
            <Pressable style={styles.seeAllButton} onPress={handleSeeAllCategories}>
              <Text style={styles.seeAllText}>See all</Text>
              <ChevronRight size={16} color={Colors.light.primary} />
            </Pressable>
          </View>
          
          <FlatList
            data={categories}
            renderItem={({ item, index }) => (
              <Pressable onPress={() => handleCategoryPress(item.id)}>
                <AnimatedCategoryCard category={item} index={index} />
              </Pressable>
            )}
            keyExtractor={(item) => item.id}
            horizontal
            showsHorizontalScrollIndicator={false}
            contentContainerStyle={styles.categoriesContainer}
          />
        </View>

        {/* Featured Products */}
        <View style={styles.section}>
          <View style={styles.sectionHeader}>
            <Text style={styles.sectionTitle}>Featured Products</Text>
            <Pressable style={styles.seeAllButton} onPress={handleSeeAllProducts}>
              <Text style={styles.seeAllText}>See all</Text>
              <ChevronRight size={16} color={Colors.light.primary} />
            </Pressable>
          </View>
          
          <View style={styles.productsGrid}>
            {featuredProducts.map((product, index) => (
              <View key={product.id} style={styles.productItem}>
                <AnimatedProductCard product={product} index={index} />
              </View>
            ))}
          </View>
        </View>

        {/* Sustainability Story */}
        <View style={styles.storySection}>
          <View style={styles.storyCard}>
            <View style={styles.storyImageContainer}>
              <Image
                source={{ uri: 'https://images.unsplash.com/photo-1542838132-92c53300491e?q=80&w=2074&auto=format&fit=crop' }}
                style={styles.storyImage}
                contentFit="cover"
              />
              <View style={styles.storyOverlay} />
            </View>
            <View style={styles.storyContent}>
              <Text style={styles.storyTitle}>Farm to Table</Text>
              <Text style={styles.storySubtitle}>
                Discover how we work directly with local farms to bring you the freshest ingredients while reducing food waste.
              </Text>
              <Pressable style={styles.storyButton}>
                <Text style={styles.storyButtonText}>Learn more</Text>
                <ChevronRight size={16} color={Colors.light.primary} />
              </Pressable>
            </View>
          </View>
        </View>

        {/* Popular Products */}
        <View style={styles.section}>
          <View style={styles.sectionHeader}>
            <Text style={styles.sectionTitle}>Popular This Week</Text>
            <Pressable style={styles.seeAllButton} onPress={handleSeeAllProducts}>
              <Text style={styles.seeAllText}>See all</Text>
              <ChevronRight size={16} color={Colors.light.primary} />
            </Pressable>
          </View>
          
          <FlatList
            data={popularProducts}
            renderItem={({ item, index }) => (
              <View style={styles.horizontalProductItem}>
                <AnimatedProductCard product={item} index={index} horizontal />
              </View>
            )}
            keyExtractor={(item) => item.id}
            horizontal
            showsHorizontalScrollIndicator={false}
            contentContainerStyle={styles.horizontalProductsContainer}
            initialNumToRender={4}
            maxToRenderPerBatch={4}
            windowSize={3}
          />
        </View>
      </ScrollView>
    </>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: Colors.light.background,
  },
  scrollContent: {
    paddingBottom: 32,
  },
  header: {
    paddingHorizontal: 20,
    paddingTop: 8,
    paddingBottom: 24,
  },
  welcomeContainer: {
    marginBottom: 8,
  },
  welcomeText: {
    fontSize: 16,
    color: Colors.light.textLight,
    fontWeight: '500',
    marginBottom: 4,
  },
  title: {
    fontSize: headerFontSize,
    fontWeight: '700',
    color: Colors.light.text,
    lineHeight: headerFontSize * 1.2,
  },
  impactBanner: {
    marginHorizontal: 20,
    marginBottom: 32,
    backgroundColor: Colors.light.primary,
    borderRadius: 16,
    padding: 20,
    shadowColor: Colors.light.primary,
    shadowOffset: { width: 0, height: 8 },
    shadowOpacity: 0.2,
    shadowRadius: 16,
    elevation: 8,
  },
  impactContent: {
    flexDirection: 'row',
    alignItems: 'center',
  },
  impactIconContainer: {
    width: 48,
    height: 48,
    borderRadius: 24,
    backgroundColor: 'rgba(255, 255, 255, 0.2)',
    justifyContent: 'center',
    alignItems: 'center',
    marginRight: 16,
  },
  impactTextContainer: {
    flex: 1,
  },
  impactTitle: {
    fontSize: 18,
    fontWeight: '700',
    color: '#FFFFFF',
    marginBottom: 4,
  },
  impactSubtitle: {
    fontSize: 14,
    color: 'rgba(255, 255, 255, 0.9)',
  },
  impactBadge: {
    width: 32,
    height: 32,
    borderRadius: 16,
    backgroundColor: '#FFFFFF',
    justifyContent: 'center',
    alignItems: 'center',
  },
  section: {
    marginBottom: 32,
  },
  sectionHeader: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    paddingHorizontal: 20,
    marginBottom: 16,
  },
  sectionTitle: {
    fontSize: 20,
    fontWeight: '700',
    color: Colors.light.text,
  },
  seeAllButton: {
    flexDirection: 'row',
    alignItems: 'center',
  },
  seeAllText: {
    fontSize: 14,
    color: Colors.light.primary,
    marginRight: 4,
    fontWeight: '600',
  },
  categoriesContainer: {
    paddingHorizontal: 20,
    paddingRight: 12,
  },
  productsGrid: {
    flexDirection: 'row',
    flexWrap: 'wrap',
    paddingHorizontal: 20,
    justifyContent: 'space-between',
  },
  productItem: {
    width: '48%',
    marginBottom: 16,
  },
  horizontalProductsContainer: {
    paddingHorizontal: 20,
    paddingRight: 4,
  },
  horizontalProductItem: {
    width: width * 0.8,
    marginRight: 16,
  },
  storySection: {
    paddingHorizontal: 20,
    marginBottom: 32,
  },
  storyCard: {
    backgroundColor: Colors.light.card,
    borderRadius: 20,
    overflow: 'hidden',
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 8 },
    shadowOpacity: 0.1,
    shadowRadius: 16,
    elevation: 8,
  },
  storyImageContainer: {
    height: 160,
    position: 'relative',
  },
  storyImage: {
    width: '100%',
    height: '100%',
  },
  storyOverlay: {
    ...StyleSheet.absoluteFillObject,
    backgroundColor: 'rgba(0, 0, 0, 0.3)',
  },
  storyContent: {
    padding: 20,
  },
  storyTitle: {
    fontSize: 20,
    fontWeight: '700',
    color: Colors.light.text,
    marginBottom: 8,
  },
  storySubtitle: {
    fontSize: 14,
    color: Colors.light.textLight,
    lineHeight: 20,
    marginBottom: 16,
  },
  storyButton: {
    flexDirection: 'row',
    alignItems: 'center',
  },
  storyButtonText: {
    fontSize: 14,
    color: Colors.light.primary,
    fontWeight: '600',
    marginRight: 4,
  },
});
import React from 'react';
import { StyleSheet, Text, View, ScrollView, Pressable } from 'react-native';
import { Stack, useRouter } from 'expo-router';
import { 
  User, 
  Settings, 
  Bell, 
  HelpCircle, 
  Info, 
  LogOut, 
  ChevronRight 
} from 'lucide-react-native';
import { Image } from 'expo-image';
import Colors from '@/constants/colors';
import { useUserStore } from '@/store/user-store';
import Button from '@/components/Button';

export default function ProfileScreen() {
  const router = useRouter();
  const { user, isLoggedIn, logout } = useUserStore();

  const handleLogin = () => {
    router.push('/login');
  };

  const handleLogout = () => {
    logout();
  };

  const handleNotificationSettings = () => {
    router.push('/notification-settings');
  };

  const handleAbout = () => {
    router.push('/about');
  };

  const menuItems = [
    {
      icon: <Bell size={20} color={Colors.light.textLight} />,
      title: 'Notification Settings',
      onPress: handleNotificationSettings,
    },
    {
      icon: <HelpCircle size={20} color={Colors.light.textLight} />,
      title: 'Help & Support',
      onPress: () => {},
    },
    {
      icon: <Info size={20} color={Colors.light.textLight} />,
      title: 'About Us',
      onPress: handleAbout,
    },
  ];

  return (
    <>
      <Stack.Screen
        options={{
          title: '',
          headerStyle: {
            backgroundColor: Colors.light.background,
          },
          headerShadowVisible: false,
        }}
      />
      <ScrollView style={styles.container} showsVerticalScrollIndicator={false}>
        {/* Header */}
        <View style={styles.header}>
          <Text style={styles.title}>Profile</Text>
        </View>

        {/* User Info */}
        {isLoggedIn && user ? (
          <View style={styles.userCard}>
            <View style={styles.avatarContainer}>
              {user.photoUrl ? (
                <Image source={{ uri: user.photoUrl }} style={styles.avatar} />
              ) : (
                <User size={24} color="#FFFFFF" />
              )}
            </View>
            <View style={styles.profileInfo}>
              <Text style={styles.name}>{user.name}</Text>
              <Text style={styles.email}>{user.email}</Text>
            </View>
          </View>
        ) : (
          <View style={styles.loginButtonContainer}>
            <Button
              title="Sign In"
              onPress={handleLogin}
              style={styles.loginButton}
            />
          </View>
        )}

        {/* Account Section */}
        <View style={styles.section}>
          <Text style={styles.sectionTitle}>Account</Text>
          {menuItems.map((item, index) => (
            <Pressable key={index} style={styles.menuItem} onPress={item.onPress}>
              {item.icon}
              <Text style={styles.menuItemText}>{item.title}</Text>
              <ChevronRight size={16} color={Colors.light.textLight} />
            </Pressable>
          ))}
        </View>

        {/* Logout */}
        {isLoggedIn && (
          <Pressable style={styles.logoutButton} onPress={handleLogout}>
            <LogOut size={20} color={Colors.light.error} />
            <Text style={styles.logoutText}>Sign Out</Text>
          </Pressable>
        )}

        {/* App Version */}
        <Text style={styles.versionText}>Version 1.0.0</Text>
      </ScrollView>
    </>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: Colors.light.background,
  },
  header: {
    paddingHorizontal: 20,
    paddingVertical: 16,
  },
  title: {
    fontSize: 24,
    fontWeight: '700',
    color: Colors.light.text,
  },
  userCard: {
    flexDirection: 'row',
    alignItems: 'center',
    backgroundColor: Colors.light.cardAlt,
    borderRadius: 12,
    padding: 16,
    marginHorizontal: 20,
    marginBottom: 24,
  },
  avatarContainer: {
    width: 60,
    height: 60,
    borderRadius: 30,
    backgroundColor: Colors.light.primary,
    justifyContent: 'center',
    alignItems: 'center',
    marginRight: 16,
  },
  avatar: {
    width: 60,
    height: 60,
    borderRadius: 30,
  },
  profileInfo: {
    flex: 1,
  },
  name: {
    fontSize: 18,
    fontWeight: '600',
    color: Colors.light.text,
    marginBottom: 4,
  },
  email: {
    fontSize: 14,
    color: Colors.light.textLight,
  },
  loginButtonContainer: {
    paddingHorizontal: 20,
    marginBottom: 24,
  },
  loginButton: {
    width: '100%',
  },
  section: {
    marginBottom: 24,
  },
  sectionTitle: {
    fontSize: 16,
    fontWeight: '600',
    color: Colors.light.primary,
    paddingHorizontal: 20,
    marginBottom: 8,
  },
  menuItem: {
    flexDirection: 'row',
    alignItems: 'center',
    paddingHorizontal: 20,
    paddingVertical: 16,
    borderBottomWidth: 1,
    borderBottomColor: Colors.light.borderLight,
  },
  menuItemText: {
    flex: 1,
    fontSize: 16,
    color: Colors.light.text,
    marginLeft: 16,
  },
  logoutButton: {
    flexDirection: 'row',
    alignItems: 'center',
    paddingHorizontal: 20,
    paddingVertical: 16,
    marginBottom: 16,
  },
  logoutText: {
    fontSize: 16,
    color: Colors.light.error,
    marginLeft: 16,
    fontWeight: '600',
  },
  versionText: {
    fontSize: 12,
    color: Colors.light.textLight,
    textAlign: 'center',
    marginBottom: 32,
  },
});
import React, { useState, useEffect } from 'react';
import {
  StyleSheet,
  Text,
  View,
  ScrollView,
  TextInput,
  Pressable,
  FlatList,
  Dimensions,
} from 'react-native';
import { Stack, useRouter } from 'expo-router';
import { Search, X, Filter, ShoppingBag } from 'lucide-react-native';
import Colors from '@/constants/colors';
import { categories } from '@/mocks/categories';
import { products } from '@/mocks/products';
import AnimatedProductCard from '@/components/AnimatedProductCard';
import CartIcon from '@/components/CartIcon';
import { Image } from 'expo-image';

const { width } = Dimensions.get('window');
const headerFontSize = width < 375 ? 20 : 24;

// Define types for category options
type CategoryWithIcon = {
  id: string;
  name: string;
  icon: React.ReactNode;
};

type CategoryWithImage = {
  id: string;
  name: string;
  image: string;
};

export default function ShopScreen() {
  const router = useRouter();
  const [searchQuery, setSearchQuery] = useState('');
  const [selectedCategory, setSelectedCategory] = useState('all');
  const [filteredProducts, setFilteredProducts] = useState(products);
  const [showFilters, setShowFilters] = useState(false);

  useEffect(() => {
    let filtered = products;

    // Filter by category
    if (selectedCategory !== 'all') {
      filtered = filtered.filter(product => product.category === selectedCategory);
    }

    // Filter by search query
    if (searchQuery.trim()) {
      filtered = filtered.filter(product =>
        product.name.toLowerCase().includes(searchQuery.toLowerCase()) ||
        product.description.toLowerCase().includes(searchQuery.toLowerCase()) ||
        product.tags.some(tag => tag.toLowerCase().includes(searchQuery.toLowerCase()))
      );
    }

    setFilteredProducts(filtered);
  }, [searchQuery, selectedCategory]);

  const clearSearch = () => {
    setSearchQuery('');
  };

  const handleCategorySelect = (categoryId: string) => {
    setSelectedCategory(categoryId);
  };

  // Create category options with proper typing
  const categoryOptions: (CategoryWithIcon | CategoryWithImage)[] = [
    { 
      id: 'all', 
      name: 'All', 
      icon: <ShoppingBag size={18} color={selectedCategory === 'all' ? '#FFFFFF' : Colors.light.text} /> 
    },
    ...categories.map(cat => ({ 
      id: cat.id, 
      name: cat.name,
      image: cat.image
    }))
  ];

  return (
    <>
      <Stack.Screen
        options={{
          title: '',
          headerStyle: {
            backgroundColor: Colors.light.background,
          },
          headerShadowVisible: false,
          headerRight: () => <CartIcon />,
        }}
      />
      <View style={styles.container}>
        {/* Header */}
        <View style={styles.header}>
          <Text style={styles.title}>Shop</Text>
          <Pressable 
            style={styles.filterButton}
            onPress={() => setShowFilters(!showFilters)}
          >
            <Filter size={20} color={Colors.light.text} />
          </Pressable>
        </View>

        {/* Search Bar */}
        <View style={styles.searchContainer}>
          <Search size={20} color={Colors.light.textLight} style={styles.searchIcon} />
          <TextInput
            style={styles.searchInput}
            placeholder="Search products..."
            value={searchQuery}
            onChangeText={setSearchQuery}
            placeholderTextColor={Colors.light.textLight}
          />
          {searchQuery.length > 0 && (
            <Pressable onPress={clearSearch} style={styles.clearButton}>
              <X size={20} color={Colors.light.textLight} />
            </Pressable>
          )}
        </View>

        {/* Category Filter */}
        <View style={styles.categoryFilterContainer}>
          <FlatList
            data={categoryOptions}
            renderItem={({ item }) => (
              <Pressable
                style={[
                  styles.categoryChip,
                  selectedCategory === item.id && styles.selectedCategoryChip
                ]}
                onPress={() => handleCategorySelect(item.id)}
              >
                {'icon' in item ? (
                  <View>{item.icon}</View>
                ) : (
                  <View style={styles.categoryImageContainer}>
                    <Image
                      source={{ uri: item.image }}
                      style={styles.categoryImage}
                      contentFit="cover"
                    />
                  </View>
                )}
                <Text
                  style={[
                    styles.categoryChipText,
                    selectedCategory === item.id && styles.selectedCategoryChipText
                  ]}
                  numberOfLines={1}
                >
                  {item.name}
                </Text>
              </Pressable>
            )}
            keyExtractor={(item) => item.id}
            horizontal
            showsHorizontalScrollIndicator={false}
            contentContainerStyle={styles.categoriesContainer}
          />
        </View>

        {/* Products Grid */}
        <ScrollView style={styles.productsContainer} showsVerticalScrollIndicator={false}>
          <View style={styles.productsGrid}>
            {filteredProducts.map((product, index) => (
              <View key={product.id} style={styles.productItem}>
                <AnimatedProductCard product={product} index={index} />
              </View>
            ))}
          </View>
          
          {filteredProducts.length === 0 && (
            <View style={styles.emptyState}>
              <Text style={styles.emptyStateTitle}>No products found</Text>
              <Text style={styles.emptyStateText}>
                Try adjusting your search or category filter
              </Text>
            </View>
          )}
        </ScrollView>
      </View>
    </>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: Colors.light.background,
  },
  header: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    paddingHorizontal: 20,
    paddingVertical: 16,
  },
  title: {
    fontSize: headerFontSize,
    fontWeight: '700',
    color: Colors.light.text,
  },
  filterButton: {
    width: 40,
    height: 40,
    borderRadius: 20,
    backgroundColor: Colors.light.cardAlt,
    justifyContent: 'center',
    alignItems: 'center',
  },
  searchContainer: {
    flexDirection: 'row',
    alignItems: 'center',
    backgroundColor: Colors.light.card,
    borderRadius: 12,
    marginHorizontal: 20,
    marginBottom: 16,
    paddingHorizontal: 12,
    height: width < 375 ? 44 : 48,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.05,
    shadowRadius: 4,
    elevation: 2,
  },
  searchIcon: {
    marginRight: 8,
  },
  searchInput: {
    flex: 1,
    height: '100%',
    fontSize: width < 375 ? 14 : 16,
    color: Colors.light.text,
  },
  clearButton: {
    padding: 4,
  },
  categoryFilterContainer: {
    marginBottom: 16,
  },
  categoriesContainer: {
    paddingHorizontal: 20,
    paddingBottom: 8,
  },
  categoryChip: {
    flexDirection: 'row',
    alignItems: 'center',
    paddingHorizontal: 16,
    paddingVertical: 10,
    borderRadius: 20,
    backgroundColor: Colors.light.card,
    marginRight: 10,
    minWidth: 100,
    maxWidth: 160,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 1 },
    shadowOpacity: 0.05,
    shadowRadius: 2,
    elevation: 1,
  },
  selectedCategoryChip: {
    backgroundColor: Colors.light.primary,
  },
  categoryImageContainer: {
    width: 24,
    height: 24,
    borderRadius: 12,
    overflow: 'hidden',
    marginRight: 8,
  },
  categoryImage: {
    width: '100%',
    height: '100%',
  },
  categoryChipText: {
    fontSize: width < 375 ? 12 : 14,
    color: Colors.light.text,
    fontWeight: '500',
    marginLeft: 8,
  },
  selectedCategoryChipText: {
    color: '#FFFFFF',
    fontWeight: '600',
  },
  productsContainer: {
    flex: 1,
    paddingHorizontal: 20,
  },
  productsGrid: {
    flexDirection: 'row',
    flexWrap: 'wrap',
    justifyContent: 'space-between',
    paddingBottom: 24,
  },
  productItem: {
    width: '48%',
    marginBottom: 16,
  },
  emptyState: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    paddingVertical: 60,
  },
  emptyStateTitle: {
    fontSize: 18,
    fontWeight: '600',
    color: Colors.light.text,
    marginBottom: 8,
  },
  emptyStateText: {
    fontSize: 14,
    color: Colors.light.textLight,
    textAlign: 'center',
  },
});
import React from 'react';
import { StyleSheet, Text, View, ScrollView, Pressable } from 'react-native';
import { Stack, useRouter } from 'expo-router';
import { Plus, CalendarClock } from 'lucide-react-native';
import Colors from '@/constants/colors';
import { useUserStore } from '@/store/user-store';
import SubscriptionCard from '@/components/SubscriptionCard';
import EmptyState from '@/components/EmptyState';

export default function SubscriptionsScreen() {
  const router = useRouter();
  const subscriptions = useUserStore((state) => state.subscriptions);
  const activeSubscriptions = subscriptions.filter(sub => sub.isActive);
  const inactiveSubscriptions = subscriptions.filter(sub => !sub.isActive);

  const handleCreateSubscription = () => {
    router.push('/create-subscription');
  };

  return (
    <>
      <Stack.Screen
        options={{
          title: '',
          headerStyle: {
            backgroundColor: Colors.light.background,
          },
          headerShadowVisible: false,
        }}
      />
      <View style={styles.container}>
        {/* Header */}
        <View style={styles.header}>
          <Text style={styles.title}>Subscriptions</Text>
          <Pressable style={styles.addButton} onPress={handleCreateSubscription}>
            <Plus size={20} color="#FFFFFF" />
          </Pressable>
        </View>

        {subscriptions.length > 0 ? (
          <ScrollView
            style={styles.subscriptionsContainer}
            showsVerticalScrollIndicator={false}
          >
            {/* Active Subscriptions */}
            <View style={styles.activeSection}>
              <Text style={styles.sectionTitle}>Active Subscriptions</Text>
              {activeSubscriptions.length > 0 ? (
                activeSubscriptions.map(subscription => (
                  <SubscriptionCard
                    key={subscription.id}
                    subscription={subscription}
                  />
                ))
              ) : (
                <Text style={styles.emptyMessage}>No active subscriptions</Text>
              )}
            </View>

            {/* Inactive Subscriptions */}
            <View style={styles.inactiveSection}>
              <Text style={styles.sectionTitle}>Paused Subscriptions</Text>
              {inactiveSubscriptions.length > 0 ? (
                inactiveSubscriptions.map(subscription => (
                  <SubscriptionCard
                    key={subscription.id}
                    subscription={subscription}
                  />
                ))
              ) : (
                <Text style={styles.emptyMessage}>No paused subscriptions</Text>
              )}
            </View>
          </ScrollView>
        ) : (
          <EmptyState
            icon={<CalendarClock size={32} color={Colors.light.primary} />}
            title="No Subscriptions Yet"
            message="Subscribe to your favorite products and have them delivered regularly."
            buttonTitle="Create Subscription"
            onButtonPress={handleCreateSubscription}
          />
        )}
      </View>
    </>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: Colors.light.background,
  },
  header: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    paddingHorizontal: 20,
    paddingVertical: 16,
  },
  title: {
    fontSize: 24,
    fontWeight: '700',
    color: Colors.light.text,
  },
  addButton: {
    width: 40,
    height: 40,
    borderRadius: 20,
    backgroundColor: Colors.light.primary,
    justifyContent: 'center',
    alignItems: 'center',
  },
  subscriptionsContainer: {
    flex: 1,
    paddingHorizontal: 20,
  },
  activeSection: {
    marginBottom: 24,
  },
  inactiveSection: {
    marginBottom: 24,
  },
  sectionTitle: {
    fontSize: 18,
    fontWeight: '600',
    color: Colors.light.text,
    marginBottom: 16,
  },
  emptyMessage: {
    fontSize: 14,
    color: Colors.light.textLight,
    fontStyle: 'italic',
    marginBottom: 16,
  },
});
